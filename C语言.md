# 一、C语言概述
### 简单C程序
```C
#include<stdio.h>
int main()
{
    int num;
    num = 1;
    printf("一个简单的测试程序");
    printf("\n");
    printf("num的值为%d",num);
}
```
* #include指令和头文件
    * #include：C语言预处理指令
    * #include<stdio.h>：将stdio.h文件中所有的内容复制到该行所在位置
* main()函数
    * C语言程序一定从`main()函数`开始执行
    * `()`用于标识函数
    * `函数`是C程序的基本模块
* 注释
    * `/*  ..... */`：多行注释
    * `//`：单行注释
* `{ ... }：花括号、函数体和块
    * 所有C函数都使用花括号标记函数的开始和结束
* 声明
    * int num：声明了一个名为num的`变量`，num叫做`标识符`,int表明num是一个整数，int叫做`数据类型`,同时也是C语言中的`关键字`
    * 变量必须先声明后使用
    * 标识符：只能由`字母、数字、下划线（_）`组成，`数字`不能放在开头位置，不能单独使用`关键字`，严格区分大小写。
    * 数据类型：计算机依据数据类型正确的存储、读取和解释数据。
* 赋值
    * num = 1：表示将1赋值给num
    * `=`：赋值符，将右边的值赋到左侧。
* printf()函数
    * printf()：标准输出函数，printf为`函数名`，`()`表明这是一个函数，括号中的内容是从`mian()函数`传递给`printf()函数`的信息，称为`参数`。
    * printf("这是一个测试程序")：调用函数时只需输入函数名，然后将所需的参数填入括号内即可。
    * printf("\n")；`\n`表示换行，称为`转义序列`
    * printf("a的值为%d",num)：`%d`为占位符，表明变量num的输出位置
* 程序由一个或多个函数组成，必须有main()函数，函数由`函数头`和`函数体`组成,函数头包括`函数名、传入的信息类型和函数返回类型`。函数体由`{}`括起来，由一系列的语句和声明组成。
```C
#include<stdio.h>
int main()
{
    int a,b;    //同时声明多个语句
    a = 3;
    b = 3;
    printf("a的值是%d，b的值是%d",a,b); //同时打印多个变量
}
```
* 多函数程序
```c
#include<tdio.h>
void sayhi();
int main()
{
    printf("你好啊");
    sayhi();
}
void sayhi()
{
    printf("Hi");
}
```
* `void sayhi();`：函数原型，定义了函数的返回值类型、函数名、参数
* `sayhi()`：函数调用
* `void sayhi() { printf("Hi");}`：函数实现
### 课后练习
* 编写程序，生成以下输出
`你好`
`你好，很高兴认识你`
`我也很高兴认识你`
第一句话在main函数中直接打印，第二句话通过调用自定义的sayhi()函数打印，第三句话通过调用sayhi2()打印
# 二、数据和C
```c
#include<stdio.h>
int main()
{
    float weight;
    float height;
    float bmi;
    printf("请输入你的体重：");
    scanf("%f",&weight);
    printf("请输入你的身高：");
    scanf("%f",&height);
    bmi = weight/(height*height);
    printf(“你的身高为%f，你的体重为%f，你的BMI为%f”,height,weight,bmi);
}
```
* 使用了新的变量声明，`float`浮点数类型
* 使用`%f`打印和读取浮点数
* scanf()函数：用于读取键盘的输入，`&`表明找到用来存储数据的变量的地址
### C语言基本数据类型
* 整数：char short int long
* 小数：float double
* 7是整数，7.0是小数
##### int类型
* 有符号整数类型
* 声明：为变量赋予名称并分配内存空间
    ```c
    int a;
    int a,b,c;
    ```
* 初始化：为变量赋初始值
    ```c
    int a = 12;
    int b = 6,c=3;
    ```
* int常量：21，32，-29
* 打印和输入int值：%d
    ```c
    int a,b,c;
    printf("请输入a的值：");
    scanf("%d",&a);
    printf("请输入b和c的值：");
    scanf("%d,%d",&b,&c);
    printf("a的值为：%d，b的值为%d，c的值为%d",a,b,c);
    ```
##### 其他整型
* short
    * %h
* long
    * %ld
* long long 
    * %lld
* unsigned short
    * %hu
* unsigned int
    * %u
* unsigned long
    * %lu
* unsigned long long
    * %llu
##### 字符类型（char）
* char本质上是整数类型，char实际存储的是数字而不是字符，其内存储的是字符的编码
* 大小为1字节
* 声明
    ```c
    char ch;
    char ch2,ch3;
    ```
* 字符常量与初始化
    ```c
    char ch = 'a';
    char ch2;
    ch2 = 'b';
    ```
    * 字符常量使用`'`引起来
* 非打印字符：无法打印出来的符号，例如换行、退格、蜂鸣等
    * 使用ASCII码，如蜂鸣的编码为7
    `char beep = 7;`
    * 使用转义字符
    `char nerf = '\n';`
* 字符打印：%c
* 符号问题：官方没有定义char到底是有符号还是无符号，取决于编译器如何实现。
##### flaot、double
* float：小数点后至少6位有效数字
    * 声明：`float a,b;`
    * 打印：%f
* double：小数点后至少10位有效数字
    * 声明：`double a,b;`
    * 打印：%f
##### 获取不同数据类型的大小
* sizeof()函数：以字节为单位给出只当类型的大小
* 打印返回结果：%ze或%u（%lu）
# 三、字符串和格式化输入输出
### 先导程序
```c
#include<stdio.h>
#include<string.h>
#define CH 365
int main()
{
    int age,length;
    char name[40];
    printf("请输入你的姓名：");
    scanf("%s",name);
    printf("请输入你的年龄：");
    scanf("%d",&age);
    length = strlen(name);
    printf("姓名：%s\n姓名长度：%d年龄：%d\n生存天数：%d",name,length,age,age*CH);
}
```
* 使用`数组`存储`字符串`
* 使用`%s`来输入和输出数组
* 使用预处理中将`CH`定义为365
* 使用strlen()函数来获取字符串的长度
### 字符串
* 使用`"`来标记字符串
* 使用`\0（空字符）`来标记字符串的结束
* 使用scanf()函数读取字符串时，使用空白符作为分隔符（空格、制表符、换行符）
* 正确区分字符和字符串
### strlen()函数
* 该函数返回字符串的实际大小
* 使用%zd打印返回值
### 常量和预处理
* 使用预处理器来定义常量
    `#define PI 3.1415926`
* 使用`const`关键字来限定变量为`只读`
    `const int a = 24;`
### printf()函数
* printf(格式字符串，待打印项1，待打印项2....)
* 常见的转换说明符
    * %c:单个字符
    * %d：有符号十进制整数
    * %f：十进制形式浮点数
    * %e：e记数法的浮点数
    * %p：指针
    * %s：字符串
    * %u：无符号十进制整数
* 常见的转换说明修饰符
    * 标记
        * -：左对齐
        * +：显示正负号
    * 数字：最小字段宽度
    * .数字：精度,用于字符串时表示待打印的字符个数
    * 搭配整型转换说明修饰符
        * h：short类型值
        * hh：signend char或unsigend char类型值
        * l：long 或unsigend long类型值
        * ll：long long 或unsigend long long类型值
        * z：表示sieze_t类型的值
    * 搭配浮点数转换说明修饰符
        * L：表示long double类型值
    ```c
    #include<stdio.h>
    #define T 956
    int main()
    {
        printf("*%d*",T);
        printf("*%2d*",T);
        printf("*%10d*",T);
        printf("*-10%d*",T);
        const double D = 3856.72;
        printf("*%f*",D);
        printf("*%4.2f*",D);
        printf("*%10.3f*",D);
    }
    ```
* 表达式或参数中的float类型会被自动转换成double类型
### scanf()函数
* 使用scanf()读取基本变量类型的值，在变量名前加&
* 使用scanf()将字符串读入字符数组中时，不使用&
