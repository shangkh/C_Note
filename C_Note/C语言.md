# C语言



## C语言基础

文件的命名为：文件名.c

```c
#include <stdio.h>

int main()
{
    const int AMOUNT = 100;
    int price = 0;
    
    printf("请输入金额（元）:");
    scanf("%d", &price);   
    
    int change = AMOUNT - price;
    printf("找您%d元。\n",  change);
    
    return 0;
}
```

- 同时定义两个变量

  ```c
  int a, b;
  ```

- int 变量类型，整数，输入时用 `%d`。**对两个整数进行运算的时候，它们的结果也只能是整数，小数部分会直接舍去，不会四舍五入**

- scanf 读取用户输入,变量名前加 & 才能识别。

- const 是一个修饰符，加在int前面，用来给这个变量加上一个const（不变的）属性。这个const的属性表示这个变量的值一旦初始化，就不能在修改了。

  - const 修饰的变量应该用全大写，表示不可修改。
  - 如果你视图对常量做修改，把它放在赋值运算符的左边，就会被编译器发现，指出为一个错误。

- 格式化输入/出

  ```c
  int a = 0;
  int b =0;
  scanf("%d %d", &a, &b);
  printf("%d + %d = %d\n", a, b, a + b);
  ```

- float 变量类型，浮点数，输入时用 `%f`。**10和10.0在C中是完全不同的数**

  - float 表示“单精度浮点数”
  - 当浮点数和整数一起进行运算的时候，C会将整数转换为浮点数，然后进行浮点数运算。

- double 变量类型，浮点数，输入时用 `%lf`，输出是用`%f`即可。double的意思是“双”，它本来是“双精度浮点数”的第一个单词，人们用来表示浮点数类型。

- 运算符(operator)： 是指进行运算的动作。

- 算子(operand)： 是指参与运算的值，这个值可能是常量，也可能是变量，还可能是一个方法的返回值。

- 优先级最高的是“单目运算”——>`+ -`，类似正负，运算的顺序”自右向左“。

- `/=`整除。

- `=` 是优先级最低的的运算符。

- 交换变量 

  ```c
  #include <stdio.h>
  
  int main()
  {
      int a = 5;
      int b = 6;
      int t;
      t = a;
      a = b;
      b = t;
      printf("a=%d,b=%d\n", a,b);
      return 0;
  }
  ```

- `++`（递增）和 `--`（递减）运算符，弹幕运算符，算子必须是变量。所用是分别为这个变量 +1 或 -1 。

  - 可以放在变量前面，叫做前缀形式，也可以放在变量的后面，叫做后缀形式。

  - a++ 的值是 a加1 以前的值，而 ++a 的值是 a加了1 以后的值，无论哪个，a自己的值都加了1。

    ```c
    #include <stdio.h>
    
    int main()
    {
    	int a;
        a = 10;
        
        printf("a++=%d\n", a++);
        printf("a=%d\n", a);
        
        printf("++a=%d\n", ++a);
        printf("a=%d\n", a);
        
        return 0;
    }
    // 结果
    a++ = 10
    a = 11
    ++a = 12
    a = 12
    ```

- 注释

  - `//`：单行注释
  - `/* */`：多行注释

### 判断

- 判断（语句以 `;` 结束）

  ```c
  if (条件)
      条件成立执行的语句;
  else
      条件不成立执行的语句;
  ```

  ```c
  if (条件)
  {
      条件成立执行的语句;
  }
  else
  {
      条件不成立执行的语句;
  }
  ```

- 嵌套

  ```c
  if (条件1)
  {
      if (条件2)
      {
          条件1、2都成立执行的语句;
      }
      else
      {
          条件1成立，条件2不成立执行的语句;
      }
  }
  else
  {
      条件1不成立执行的语句;
  }
  // ----------------------------------------------------------------
  if (条件)
      if (条件)  //else会匹配这个if
      	条件成立执行的语句;
  else  // 这里的else会匹配最近的if，和缩进无关
      条件不成立执行的语句;
  // ----------------------------------------------------------------
  if (条件)
      if (条件)
      	条件成立执行的语句;
  	else  // 这里的else会匹配第二个if
          条件不成立执行的语句;
  else  // 这里的else会匹配第一个if
      条件不成立执行的语句;
  ```

- 级联的 `if-else if`

  ```c
  if (条件1)
  {
      条件1成立执行的语句;
  }
  else if (条件2)
  {
      条件1不成立，条件2成立执行的语句;
  }
  else
  {
      条件1、2都不成立执行的语句;
  }
  ```

- 多分支`switch-case`

  - switch语句可以看作是一种基于计算法的跳转，计算控制表达式的值后，程序会跳转到相匹配的case（分支标号）处。
  - 分支标号只是说明switch内部位置的路标，在执行完分支中的最后一条语句后，如果后面没有break，就会顺序执行到下面的case里面去，直到遇到一个break，或者switch结束为止。

  ```c
  switch (控制表达式)  // 控制表达式必须是 int 类型
  {
  case 常量:  // 常量可以是常数，也可以是常数计算表达式
      语句;
  	break;
  case 常量:
      语句;
  	break;
  ...
  default 常量:
      语句;
  	break;
  }
  ```

#### 循环

- 循环 while

  ```c
  int n = 0;
  while (条件) {
      条件成立执行的语句;
      n++;
  }
  ```

- 循环 do-while

  - 在进入循环的时候不做检查，而是在执行完一轮循环体的代码之后，再来检查循环的条件是否满足，如果满足则继续下一轮循环，不满足则结束循环。
  - do-while循环和while循环很像，区别是在循环体执行结束的时候才来判断条件。也就是说，无论如何，循环都会执行至少一次，然后再来判断条件。与while循环相同的是，条件满足是执行循环，条件不满足是结束循环。

  ```c
  do
  {
      循环体语句;
  } while (循环条件);
  ```

- 随机数：rand()

  ```c
  #include <stdlib.h>
  int a = rand();
  ```

- 时间：tiime()

  ```c
  #include <time.h>
  srand(time());
  ```

- for 循环

  - for循环像一个计数循环：设定一个计数器，初始化它，然后在计数器到达某值之前，重复执行循环体，而每执行一轮循环，计数器值以一定步进进行调整，比如加i或者减i
  - for循环的每一个表达式都是可以省略的：`for ( ;条件; ) == while ( 条件 )`
  - `for == while` 

  ```c
  for (初始动作, 循环条件, 每轮的动作) {
      循环体;
  }
  
  // n!
  int n = 0;
  for ( i=1; i<n; i++ ) {
      fact *= i;
  }
  ```

- break：跳出循环

- continue：跳过循环这一轮剩下的语句进入下一轮

- 跳出多重循环

  - 接力break

    ```c
    int exit = 0;
    for () {
        for () {
            for () {
                ...
                exit = 1;
                break;
            }
            if ( exit == 1 ) break;
        }
        if ( exit == 1 ) break;
    }
    ```

  - goto:调到任意位置

    ```c
    for () {
        for () {
            for () {
                ...
                goto out;
            }
        }
     }
    out:
    ```



## C语言的类型

- C语言的变量，必须：
  - 在使用前定义，并且，
  - 确认类型
  - C以后的语言向两个方向发展：
    - C++/Java更强调类型，对类型的检查更严格
    - JavaScript、Python、PHP不看重类型，甚至不需要事先定义
  - 支持强类型的观点认为明确的类型有助于尽早发现程序中的简单错误
  - 反对强类型的观点认为过于强调类型迫使程序员面对底层、实现而非事务逻辑
  - C语言需要类型，但是对类型检查并不足够

- C语言的类型（long long、long double、bool是C99的类型）

  - 整数
    - char、short、int、long、long long
  - 浮点数
    - float、double、long double
  - 逻辑
    - bool
  - 指针
  - 自定义类型

- 类型有何不同

  - 类型名称：int、long、double
  - 输入输出时的格式化：%d、%ld、%lf
  - 所表达的数的范围：char<short<int<float<double
  - 内存中所占据的大小：1个字节到16个字节
  - 内存中的表达形式：二进制数（补码）、编码

- int采用二进制数（补码），自然二进制数，两个整数可以在加法器中直接进行运算

- 浮点数采用编码，不是自然二进制数，编码意味着不能直接来运算

- sizeof：是一个运算符，给出某个类型或变量在内存中所占据的字节数，

  ​	      是静态运算符，它的结果在编译时刻就决定了

  ​	      不要在sizeof的括号中做运算，这些运算不会做的

  - 格式化输出使用：`%lu` 
  - sizeof(int)
  - sizeof(a)    a是变量

#### 整数

- 整数

  - char：1字节（8bytes）
  - short：2字节
  - int：取决于编译器（CPU），通常的意义是“1个字”
  - long：取决于编译器（CPU），通常的意义是“1个字”
  - long long：8字节
- int就是用来表示寄存器的大小
- 整数的计算机内部表达

  - 负数的内部表达
    - 二进制负数
      - 1个字节可以表达的数：
        - 00000000 — 11111111（0-255）
      - 三种方案
        1. 仿照十进制，有一个特殊的标志表示复数
        2. 取中间的数为0，如10000000表示0，比它小的是复数，比它大的是正数
        3. *补码
      - 补码
        - 考虑-1，我们希望 -1 + 1 —> 0。如何能做到？
          - 0 —> 00000000
          - 1 —> 11111111
          - 11111111 + 00000001 —> 100000000（计算机多余的bytes会省略，1会被省略，所以运算的结果为：00000000）
        - 因为 0 - 1 —> -1，所以，-1=
          - (1)00000000 - 00000001 —> 11111111
          - 11111111被当做纯二进制看待时，是 255，被当做补码看待时是 -1
        - 同理，对于 -a ，其补码就是 0-a，实际是 2^n^ - a，n是这种类型的位数
        - 补码的意义就是拿补码和原码可以加出一个溢出的“零”
- 整数的范围：

  - char：1字节：-128~127
  - short：2字节：-32768~32767
  - int：取决于编译器（CPU），通常的意义是“1个字”
  - long：4字节
  - long long：8字节
- unsigned：表示这个整数不以补码的形式表示负数，这个整数没有负数部分，只有0和正整数部分，当用unsigned的时候，所表达的整数部分会扩大一倍。

  - unsigned char = 255
  - 如果一个字面量常数想要表达自己是unsigned，可以在后面加u或U
    - 255U
  - 用l或L表示long(long)
  - *unsigned的初衷并非扩展数能表达的范围，而是为了做纯二进制运算，主要是为了移位
- 整数的格式化

  - 整数的输入输出
    - 只有两种形式：int或long long
    - 比int小的用int的格式化，比int大的用long long的格式化
      - %d：int
      - %u：unsigned
      - %ld：long long
      - %lu：unsigned long long
- 8进制和16进制

  - 一个以0开头的数字字面量是8进制
  - 一个以0x开始的数字字面量是16进制
  - %o用于8进制，%x用于16进制
  - 8进制和16进制只是如何把数字表达为字符串，与计算机内部如何表达数字无关
  - 16进制很适合表达二进制数据，因为4位二进制正好是一个16进制位
  - 8进制的一位数字正好表达3位二进制
    - 因为早期计算机的字长是12 的倍数，而非8
- 选择整数类型

  - 为什么整数要有那么多种？
    - 为了准确表达内存，做底层程序的需要
  - *没有特殊需要，就用int
    - 现在的CPU的字长普遍是32位或64位，一次内存读写就是一个int，一次计算也是一个int，选择更短的类型不会更快，甚至可能更慢
    - *现代的编译器一般会设计内存对齐，所以更短的类型实际在内存中有可能也占据一个int的大小 （虽然sizeof告诉你更小）
  - unsigned与否只是输出的不同，内部计算是一样的

#### 浮点类型

- 浮点类型

  |  类型  | 字长 | 范围  | 有效数字 |
  | :----: | :--: | :---: | :------: |
  | float  |  32  | 公式1 |    7     |
  | double |  64  | 公式2 |    15    |

  $$
  公式1~~~~~~~~~~~~~~~~~~~~~~~~~~~~\pm(1.20*10^{-38}~3.40*10^{38},0,\pm inf(无穷大),nan
  $$

  $$
  公式2~~~~~~~~~~~~~~~~~~~~~~~~~~~~\pm(2.2*10^{-308}~1.79*10^{308},0,\pm inf(无穷大),nan
  $$

- 浮点的输入输出

  |  类型  | scanf |                           printf                            |
  | :----: | :---: | :---------------------------------------------------------: |
  | float  |  %f   | %f，%e（%e输出一个科学计数法表示的数，e或E ，如 -5,67E+16） |
  | double |  %lf  |                           %f，%e                            |

- 输出精度

  - 在%和f之间加上`.n`可以指定输出小数点后几位，这样的输出是做4舍5入的

- 超过范围的浮点数

  - printf输出inf表示超过范围的浮点数：$\pm∞$
  - printf输出nan表示不存在的浮点数

- 浮点数的运算时没有精度的

  - 带小数点的字面量是double而非float
  - float需要用f或F后缀来表名身份（如：a = 1.345f）

- fabs()：取绝对值

- *浮点数的内部表达

  ![1550082316668](D:\1文件\MD文档\C_image\浮点数内部表达示意图.png)

  - 浮点数在计算时是由专用的硬件部件实现的
  - 现代的CPU会带着专门计算浮点数的硬件，该硬件会将浮点数解码进行计算后在编码返回
  - 计算double和float所用的硬件部件是一样的

- 选择浮点类型

  - *如果没有特殊需要，只使用double
  - 现代CPU能直接对double做硬件运算，性能不会比float差，在64位的机器上，数据存储的速度也不比float慢

#### 字符类型

- 字符类型

  - char是一种整数，也是一种特殊的类型：字符。这是因为：
    - 用单引号表示的字符字面量：'a', '1'
    - ''也是一个字符
    - printf和scanf里用%c来输入输出字符

- 字符的输入输出

  - 输入：char c = '1';
    - scanf("%c", &c); ——> 1
    - scanf("%d", &i); c = 1; ——> 49
  - '1'的ASCII编码是49，所以当 c == 49 时，它代表'1'

- 字符计算

  - 一个字符加一个数字得到ASCII码表中那个数之后的字符
  - 两个字符的减，得到它们在表中的距离

- 大小写转换

  - 字母在ASCII表中是顺序排列的
  - 大写字母和小写字母是分开排列的，并不在一起
    - 'a' - 'A' 可以得到两段之间的距离，于是
      - a + 'a' - 'A' 可以把一个大写字母变成小写字母
      - a + 'A' - 'a' 可以把一个小写字母变成大写字母

- 逃逸字符

  - 用来表示无法印出来的控制字符或特殊字符，它由一个反斜杠 "\" 开头，后面跟上另一个字符，这两个字符合起来，组成了一个字符

    ![](D:\1文件\MD文档\C_image\逃逸字符.png)

  - 制表位

    - 每行固定的位置
    - 一个 \t 是的输出从下一个制表位开始
    - 用 \t 才能使得上下两行对其

- 自动类型转换

  - 当运算符的两边出现不一致的类型时，会自动转换成较大的类型
    - 大的意思是能表达的数的范围更大
    - char —> short —> int —> long —> long long
    - int —> float —> double
  - 对于printf，任何小于int的类型会被转换成int；float会被转换成double
  - 但是scanf不会，要输入short，需要 %hd

- 强制类型转换

  - 要把一个量强制转换成另一个类型（通常是较小的类型），需要：
    - (类型)值
      - 如：(int)10.2
  - 注意这时候的安全性，小的变量不总能表达大的量
    - 如：(short)32768 —> -32768 ——> short的最大值是32767
  - *强制类型转换，只是从那个变量计算出了一个新的类型的值，它并不改变那个变量，无论是值还是类型都不改变
  - 强制类型转换的优先级高于四则运算

#### 逻辑类型：bool

- #include <stdbool.h>
- 之后就可以使用bool和true、false
- 输出用 "%d"

#### 逻辑运算

- 逻辑运算啊是对逻辑量进行的运算，结果只有0或1

- 逻辑量是关系运算或逻辑运算的结果

  | 运算符 |  描述  |   示例   |                             结果                             |
  | :----: | :----: | :------: | :----------------------------------------------------------: |
  |   ！   | 逻辑非 |   ！a    |     如果a是true结果就是false；如果阿是false结果就是true      |
  |   &&   | 逻辑与 |  a && b  |        如果a和b都是true，结果就是true；否则就是false         |
  |  \|\|  | 逻辑或 | a \|\| b | 如果a和b有一个是true，结果为true；两个都是false，结果为false |

- TRY

  - 表达数学中的区间
    - x > 4 && x < 6
  - 判断一个字符c是否是大写字母
    - c >= 'A' && c <= 'Z'
  - 年龄不小于20
    - !(age < 20)

- *优先级

  - ! > && > ||

- 短路

  - 逻辑运算是自左向右进行的，如果左边的结果已经能够决定结果了，就不会做右边的计算
    - 对于&&，左边是false时就不做右边了
    - 对于||，左边是true时就不做右边了
  - *不要把赋值，包括复合赋值组合进表达式

#### 运算符优先级

![](D:\1文件\MD文档\C_image\运算符优先级.png)

#### 条件运算符

- 条件 ? 条件满足时候的值 : 条件不满足时候的值

- count = (count >20) ? count -10 : count + 10;     相当于

  ```c
  if ( count > 20 )
      count = count - 10;
  else
      count = count + 10;
  ```

- 优先级

  - 条件运算符的优先级高于赋值运算符，但是低于其他运算符

- 嵌套条件表达式（不希望使用嵌套的条件表达式）

  - count = (count > 20 ) ? (count < 50) ? count -10 : count -5 :(count < 10 ) ? count + 10 : count + 5;
  - 条件运算符是自右向左结合的
    - w < x ? x + w : x < y ? x : y

#### 逗号运算符

- 逗号运来连接两个表达式，并以其右边的表达式的值作为它的结果。逗号的优先级是所有的运算符中最低的，所以它两边的表达式会先计算；逗号的组合关系是自左向右，所以左边的表达式会先计算，而右边的表达式的值就留下来作为逗号运算的结果。
- 在for中使用
  - for (i=0, j=10; i<j; i++, j--)......



## 函数

- “代码复制”是程序质量不良的表现

- 函数是一块代码，接收零个或多个参数，做一件事情，并返回零个或一个值

- 函数定义：函数头 + 函数体

  - 函数头：返回类型 + 函数名 + ( 参数表 )
    - 参数表：参数用 `,` 隔开；每一个参数都是，类型 + 名字，一对

  ```c
  void sum(int begin, int end)						//函数头
  {													/*函数体
      int i;
      int sum = 0;
      for ( i=begin; i<=end; i++ ){
          sum += i;
      }
      printf("%d到%d的和是%d\n", begin, end, sum);	  函数体*/
  }								
  ```

- 调用函数

  - 函数名(参数值);
  - `()`起到了表示函数调用的重要作用
    - 即使函数没有参数也需要`()` 
    - 如果有参数，则需要给出正确的数量和顺序
    - 这些值会被按照顺序依次用来初始化函数中的参数

- 函数返回

  - 函数知道每一次哪里调用它，会返回到正确的地方

- 从函数中返回值

  - return停止函数的执行，并送回一个值
    - return;
    - return 表达式;
  - 一个函数里可以出现多个return语句，但是不符合单一出口原则，不建议使用
  - 从函数中返回的值
    - 可以赋值给变量
    - 可以再传递给函数
    - 甚至可以丢弃

- 没有返回值的函数

  - void 函数名(参数表)
  - 不能使用带值的return
    - 可以没有return
  - 调用的时候不能做返回值的赋值

- 如果函数有返回值，则必须使用带值的return

#### 函数原型

- 函数先后关系

  - 把函数写在main函数上面，是因为：
  - C的编译器自上而下顺序分析代码
  - 如果要将函数写在main函数的下面，需要进行函数原型的声明

- 函数的原型声明

  - 声明不是函数，只是告诉编译器函数的样子

  ![](D:\1文件\MD文档\C_image\函数的原型声明.png)

- 函数头，以分号`;`结尾，就构成了函数的原型

- 函数原型的目的是告诉编译器这个函数章什么样子

  - 名称
  - 参数（数量及类型）
  - 返回类型

- 旧标准习惯把函数原型写在调用它的函数里面，

- 现在一般写在调用它的函数前面

- 函数原型可以不写参数的名字，但是一般任然写上

#### 参数传递

- 调用函数
  - 如果函数有参数，调用函数是必须传递给它数量、类型正确的值
  - 可以传递给函数的值是表达式的结果，这包括：
    - 字面量
    - 变量
    - 函数的返回值
    - 计算的结果
  - 调用函数时给的值与参数的类型不匹配是C语言传统上最大的漏洞
  - 编译器总是悄悄替你包类型转换好，但是这很可能不是你所期望的
  - 后续的语言，C++/Java在这方面很严格
- 调用函数传过去的到底是什么？
  - C语言在调用函数时，永远只能传值给函数

- 传值
  - 每个函数有自己的变量空间，参数也位于这个独立的空间中，和其他函数没有关系
  - 过去，对于函数参数表中的参数，叫做“形式参数”，调用函数时给的值，叫做“实际参数”
  - 由于容易让初学者误会实际参数就是实际在函数中进行计算的参数，误会调用函数的时候把变量而不是值传进去了，所以不建议继续用这种古老的方式来称呼它们
  - 我们认为，它们是参数和值的关系

#### 本地变量

- 函数的每次运行，就产生了一个独立的变量空间，在这个空间中的变量，时函数的这次运行所独有的，称为本地变量
- 定义在函数内部的变量就是本地变量
- 参数也是本地变量

#### 本地变量的规则

- 本地变量是定义在块内的
  - 它可以是定义在函数的块内
  - 也可以定义在语句的块内
  - 甚至可以随便拉一对大括号来定义变量
- 程序运行进入这个块之前，其中的变量是不存在的，离开这个块，其中的变量就消失了
- 块外面定义的变量在里面仍然有效
- 块里面定义了和外面同名的变量则掩盖了外面的
- 不能在一个块内定义同名的变量
- 本地变量不会被默认初始化
- 参数在进入函数的时候被初始化了

#### 变量的生存期和作用域

- 生存期：什么时候这个变量开始出现了，到什么时候它消亡了
- 作用域：在（代码的）社么范围内可以访问这个变量（这个变量可以起作用）
- 对于本地变量，这两个问题的答案时统一的：大括号内————块

#### 函数庶事

- 没有参数时
  - void f(void);
    - 明确的告诉编译器这个函数不接收任何参数
  - void f();
    - 在传统的C中，它表示f函数的参数表未知，并不表示没有参数
- 逗号运算符
  - 调用函数时的圆括号里的逗号都是标点符号，不是运算符
    - f(a,b)  逗号是标点符号
    - f((a,b))  逗号是逗号运算符
- C语言不允许函数的嵌套定义，在一个函数里可以放另一个函数的声明，但不能放另一个函数的body
- int i,j,sum(int a, int b);
  - 定义了int型的变量i和j，声明说sum函数要两个int作为参数并且返回一个int，
  - 这样写是可以的，但是不建议，C语言接受这样的写法
- return(i);
  - 这是一个语句：return + 表达式，这样写的`()`其实没有任何意义，这样写没有错，但是会让人误解return是一个函数，i是return函数的参数，不要这样写
- 关于main
  - int main()也是一个函数
  - return的0是有人看的
    - Windows：if errorlevel 1 ...
      - 批处理文件，bat文件，在批处理文件里面调用程序，跟上一句`if errorlevel 1`,如果程序返回的是1的话去做什么什么事情
      - 传统上一个程序如果返回0，表示正常的运行结束了，如果返回的是任何非0的值，它是有错的
    - Unix Bash：echo $?
      - `echo $?`：可以看到程序返回的结果
    - Csh：echo $status



## 数组

#### 数组

- 定义数组
  - `<类型> 变量名称[元素数量]`
    - int grades[100];
    - double weight[20];
  - 元素数量必须是整数
  - C99之前：元素数量必须是编译时刻确定的字面量
- 数组是一种容器（放东西的东西），特点是：
  - 其中所有的元素具有相同的数据类型
  - 一旦创建，不能改变大小
  - *（数组中的元素在内存中是连续一次排列的）
- int a[10];
  - 一个int的数组
  - 10个单元：a[0],a[1],...,1[9]
  - 每个单元就是一个int类型的变量
  - 可以出现在赋值的左边或右边，右边是读出，左边是写入
    - a[2] = a[1] + 6
  - *在赋值左边的叫做左值
- 数组的单元
  - 数组的每个单元就是数组类型的一个变量
  - 使用数组时放在[]中的数字叫做下标或索引，下标从0开始计数
- 有效的下标范围
  - 编译器和运行环境都不会检查数组下标是否越界，无论是对数组单元做读还是写
  - 一旦程序运行，越界的数组访问可能造成问题，导致程序崩溃
    - segmentation fault
  - 但是也可能运气好，没造成严重的后果
  - 所以这是程序员的责任来保证程序只使用有效的下标值：[0, 数组的大小-1]
- 长度为0的数组
  - int a[0]
  - 可以存在，但是无用

#### 数组的运算

- 数组的集成初始化

  - int a[] = {2,4,6,7,1,3,5,9,11,13,23,14,32,};
  - 直接用大括号给出数组的所有元素的初始值
  - 不需要给出数组的大小，编译器替你数数

- C99：集成初始化时的定位

  ```c
  int a[10] = {
      [0] = 2, [2] = 3, 6,
  };
  {2,0,3,6,0,0,0,0,0,0}
  ```

  - 用[n]在初始化数据中给出定位
  - 没有定位的数据接在前面的位置后面
  - 其他位置的值补零
  - 也可以不给出数组大小，让编译器算
  - 特别适合初始数据稀疏的数组

- 数组的大小

  - sizeof给出整个数组所占据的内容的大小，单位是字节

  - `sizeof(a)/sizeof(a[0])`
    - sizeof(a[0])给出数组中单个元素的大小，于是相除就得到了数组的单元个数
    - 这样的代码，一旦修改数组中的数据，不需要修改遍历的代码

- 数组的赋值

  - 数组变量本身不能被赋值：不能将一个数组变量直接赋值给另一个数组变量

    ```c
    // 这样是错误的
    int a[] = {2,4,6,7,1,3,5,9,11,13,23,14,32,};
    int b[] = a
    ```

  - 要把一个数组的所有元素交个另一个数组，必须采用遍历

    ```c
    for ( i=0; i<length; i++ ) {
        b[i] = a[i];
    }
    ```

- 遍历数组

  - 通常都是使用for循环，让循环变量i从0到<数组的长度，这样循环体内最大的i正好是数组最大的有效下标
  - 常见错误是：
    - 循环结束条件是 <= 数组长度，或；
    - 离开循环后，继续用i的值来做数组元素的下标！

- 数组作为函数参数时，往往必须再用另一个参数来传入数组的大小

  - 数组作为函数的参数时：
    - 不能在[]中给出数组的大小
    - 不能再利用sizeof来计算数组的元素个数！


#### 二位数组

- 定义二维数组

  - `<类型> 变量名称[元素数量][元素数量]`
    - int grades[100];
    - double weight[20];
  - 元素数量必须是整数

- 二维数组的初始化

  ```c
  int a[][5] = {
      {0,1,2,3,4},  // 里面的{}可以省略
      {2,3,4,5,6},
  }
  ```

  - 列数是必须给出的，函数可以有编译器来数
  - 每行一个`{}`，逗号分隔
  - 最后的逗号可以存在，有古老的传统
  - 如果省略，表示补零
  - C99：也可以用定位



## 指针

- 运算符 &
  - scnaf("%d", &i); 里的&
  - 作用：获取变量的地址，它的操作数必须是变量
  - 地址的大小是否与int相同取决于编译器
    - int i; printf("%p\n", &i);
    - `%p`会把这个值作为一个地址来输出，输出的时候会在前面加`0x`，并且以十六进制的方式输出

- &不能取的地址
  - 必须对一个变量取地址，如果右边不是一个变量就没法取地址
  - &不能对没有地址的东西取地址，如：
    - &(a+b)
    - &(a++)
    - &(++a)

- 一个指针类型的变量就是保存地址的变量

  ```c
  int i;
  int* p = &i;  // * 表示p是指针，通常用p表示一个指针
  int* P,q;  // *是加给p的，有没有空格都是
  int *p,q;
  ```

- 作为参数的指针

  - void f(int *p);
  - 在被调用的时候得到了某个变量的地址：
    - int i = 0; f(&i);
  - 在函数里面可以通过这个指针访问外面这个i

- 访问那个地址上的变量 `*` 

  - `*`是一个单目运算符，用来访问指针的值所表示的地址上的变量
  - 可以做右值也可以做左值
    - int k = *p;
    - *p = k + 1;

- *左值之所以叫左值

  - 是因为出现在赋值号左边的不是变量，而是值，是表达式计算的结果：
    - a[0] = 2;
    - *p = 3;
  - 是特殊的值，所以叫左值

- 指针的运算符 `& *`

  - 互相反作用
    - *&yptr —> *(&yptr) —> *(yptr的地址) —> 得到那个地址上的变量 —> yptr
    - &*yptr —> &(*yptr) —> &(y) —> 得到y的地址，也就是yptr —> yptr

- 传入地址

  - int i; scanf("%d", i);
  - 编译不一定会报错，但运行一定会报错
  - 32位的编译器会认为输入的int，就是地址

#### 指针的使用

- 交换两个变量的值

  ```c
  void swap(int *pa, int *pb)
  {
      int t = *pa;
      *pa = *pb;
      *pb = t;
  }
  ```

- 函数返回多个值

  - 函数返回多个值，某些值就只能通过指针返回
    - 传入的参数实际上是需要保存带回的结果的变量
  - 函数返回运算的状态，结果通过指针返回
    - 常用的套路是让函数返回特殊的不属于有效范围内的值来表示出错：
      - -1或0（在文件操作会看到大量的例子）
    - 但是当人和我数值都是有效的可能结果时，就得分开返回
      - 后续的语言（C++，Java）采用了异常机制来解决这个问题

#### 指针最常见的错误

- 定义了指针变量，还没有指向任何变量，就开始使用指针

#### 函数与数组

- 传入函数的数组成了什么？

  - 函数参数表中的数组实际上是指针
    - sizeof(a) == sizeof(int*)
    - 但是可以用数组的运算符`[]`进行运算

- 数组参数

  - 以下四种函数原型是等价的：
    - int sum(int *ar, int n);
    - int sum(int *, int);
    - int sum(int ar[], int n);
    - int sum(int [], int);

- #### 数组变量是特殊的指针

  - 数组变量本身表达地址，所以
    - int a[10]; int*p=a; // 无需用&取地址
    - 但是数组的单元表达的是变量，需要用&取地址
    - a == &a[0]  // a的地址就是a[0]的地址
  - `[]`运算符可以对数组做，也可以对指针做：
    - p[0] <==> a[0]
  - `*`运算符可以对指针做，也可以对数组做：
    - *a = 25;
  - 数组变量是const的指针，所以不能被赋值
    - int a[] <==> int * const a = ...

- 指针与const（只适用于C99）

  - const是修饰符，加在变量的前面表示这个变量不能被修改
  - 指针是一种变量
  - 指正变量里有两个东西
    - 指针本身
    - 指针所指的那个变量
  - 指针本身可以是const，指针所指的那个变量也可以是const
  - 指针是const
    - 表示一旦得到了某个变量的地址，不能再指向其他变量
      - int * const q = &i;  // q是const
        - q的值不能被改变
        - q的值就是i的地址
        - 就是q指向i这个事实不能被改变，也就是q不能再指向别人了，它们之间的关系是永久的
      - *q = 26;  // OK
      - q++;  // ERROR
  - 所指是const
    - 表示不能通过这个指针去修改那个变量（并不能使得那个变量成为const）
      - const int *p = &i;  // 不能通过\*p去修改i的值
      - *p = 26;  // ERROR (\*p)是const
      - i = 26;  // OK
      - p = &j;  // OK
  - 判断哪个被const了的标志是const在`*`的前面还是后面
    - const在`*`的前面表示它所指的东西不能被修改
      - const int* p1 = &i;
      - int const* p2 = &i;
    - const在`*`的后面表示它指针不能被修改
      - int *const p3 = &i;
  - 转换
    - 总是可以把一个非const的值转换成const的
      - void f(const int* x);  //表示在f函数中，不会动指针指的值
      - int a = 15;
      - f(&a);  // OK
      - const int b = a;
      - f(&b);  // OK
      - b = a + 1;  // ERROR
    - 当要传递的参数的类型比地址大的时候，这是常用的手段：
      - 既能用比较少的字节数传递值给参数，又能避免函数对外面的变量的修改
  - const 数组
    - const int a[] = {1,2,3,4,5,6,};
    - 数组变量已经是const指针了，这里的const表明数组的每个单元都是const int
    - 所以必须通过初始化进行赋值
  - 保护数组值
    - 因为把数组传入函数时传递的是地址，所以那个函数内部可以修改数组的值
    - 为了保护数组不被函数破坏，可以设置参数为const
      - int sum(const int a[], int length)

#### 指针运算

- 给一个指针加1表示要让指针指向下一个变量 ——> 指针地址 + sizeof(类型)
  - int a[10];
  - int *p = a;
  - *(p + 1) <==> a[1]
- 如果指针不是指向一片连续分配的空间，如数组，则这种运算没有意义
- 这些算数运算可以对指针做：
  - 给指针加、减一个整数（+,+=,-,-=）
  - 递增递减（++/--)
  - 两个指针相减 ——> 两个指针地址的差 / sizeof(类型) ——> 两个地址间有几个这样的类型在
- *p++
  - 取出p所指的那个数据来，完事之后顺便把p移到下一个位置去
  - *的优先级虽然高，但是没有++高
  - 常用于数组类的连续空间操作
  - 在某些CPU上，这可以直接被翻译成一条汇编命令
- 指针比较
  - <,<=,==,>,>=,!=都可以对指针做
  - 就是比较它们在内存中的地址
  - 数组中的单元的地址肯定是线性递增的
- 0地址（系统会分配虚拟内存，使每个使用进程有0地址）
  - 当然你的内存中有0地址，但是0地址通常是个不能随便碰的地址
  - 所以你的指针不应该具有0值
  - 因此可以用0地址来表示特殊的事情：
    - 返回的指针是无效的
    - 指针没有被真正初始化（先初始化为0）
  - NULL是一个预定定义的符号，表示0地址（必须全部大写）
    - 有的编译器不愿意你用0来表示0地址，想要用0地址使用NULL
- 指针的类型
  - 无论指向什么类型，所有的指针的大小都是一样的，因为都是地址
  - 但是指向不同类型的指针是不能直接互相赋值的
  - 这是为了避免用错指针
- 指针的类型转换
  - void* 表示不知道指向什么东西的指针
    - 计算是与 char* 相同（但不相通）
  - 指针也可以转换类型
    - int *p = &i; void\*q = (void\*)p;
  - 这并没有改变p所指的变量的类型，而是让后人用不同的眼光通过p看它所指的变量
    - 我不在当你是int，我认为你就是个void
- （总结）用指针来做什么
  - 需要传入较大的数据是用作参数
  - 传入数组后对数组做操作
  - 函数返回不止一个结果
    - 需要用函数来修改不止一个变量
  -  动态申请内存的时候

#### 动态内存分配

- 输入数据

  - 如果输入数据时，先告诉你个数，然后在输入，要记录每个数据

  - C99可以用变量做数组定义的大小，C99之前呢？

    - 必须使用动态内存分配

    - `int *a = (int*)malloc(n*sizeof(int));`

      ```c
      #include <stdio.h>
      #include <stdlib.h>
      
      int main(void)
      {
          int number;
          int* a;
          int i;
          printf("输入数量：");
          scanf("%d", &number);
          // int a[number]  C99
          a = (int*)malloc(number*sizeof(int));
          for ( i=0; i<number; i++ ) {
              scanf("%d", &a[i]);
          }
          for ( i=number-1; i>=0; i-- ) {
              printf("%d", a[i]);
          }
          free(a);
          
          return 0;
      }
      ```

- malloc

  - #include <stdlib.h>
  - void* mallloc(size_t size);
  - 向malloc申请的空间的大小是以字节为单位的
  - 返回的结果是void*，需要类型转换为自己需要的类型
    - (int*)malloc(n\*sizeof(int))
  - 没空间了？
    - 如果申请失败则返回0，或者叫做NULL

- free()

  - 把申请得来的空间还给“系统”
  - 申请过的空间，最终都应该要还
  - 只能换申请来的空间的首地址
  - 常见问题
    - 申请了没free ——> 长时间运行内存逐渐下降
    - free过了再free
    - 地址变过了，直接去free



## 字符串

- 字符数组

  - char word[] = {'H','e','l','l','o','!'};

    | word[0] |  H   |
    | :-----: | :--: |
    | word[1] |  e   |
    | word[2] |  l   |
    | word[3] |  l   |
    | word[4] |  o   |
    | word[5] |  !   |

  - 这不是C语言的字符串，因为不能用字符串的方式做计算

- 字符串

  - char word[] = {'H','e','l','l','o','!','\0'};

    | word[0] |  H   |
    | :-----: | :--: |
    | word[1] |  e   |
    | word[2] |  l   |
    | word[3] |  l   |
    | word[4] |  o   |
    | word[5] |  !   |
    | word[6] |  \0  |

#### 字符串

- 以0（整数0）结尾的一串字符
  - 0或'\0'是一样的，但是和'0'不同；0是int类型，4个字节，'\0'一定是一个字节
- 0标志字符串的结束，但它不是字符串的一部分
  - 计算字符串长度的时候不包含这个0
- 字符串以数组的形成存在，以数组或指针的形式访问
  - 更多的是以指针的形式
- string.h 里有很多处理字符串的函数

#### 字符串变量

- char *str = "Hello";
  - 一个叫 str 的指针指向了一个字符数组，这个数组里面放的内容是 Hello
- char word[] = "Hello";
  - 这里有一个字符数组里面的内容是 Hello
- char line[10] = "Hello";
  - 有个叫 line 的字符数组，这个line与10个字节那么大，里面放了Hello，Hello在这个字符数组中占据6个字节（结尾的'\0'）

#### 字符串常量

- "Hello" 由 "" 括起来的叫字符串的字面量或者字符串常量

- "Hello"会被编译器变成一个字符数组放在某处，这个数组的长度是6，结尾还有表示结束的0

- 两个相邻的字符串常量会被自动连接起来

- `char* s = "Hello, world!";`

  - `s`是一个指针，初始化为指向一个字符串常量
    - 由于这个常量所在的地方，所以实际上`s`是`const char* s`，但是由于历史的原因，编译器接受不带`const`的写法
    - 但是试图对s所指的字符串做写入会导致严重的后果
  - 如果需要修改字符串，应该用数组：
    - `char s[] = "Hello, world!";`
  - 指针还是数组？
    - `char *str = "Hello";`
      - 指针：这个字符串不知道在哪里
        - 处理函数
        - 动态分配空间
    - `char word[] = "Hello";`
      - 数组：这个字符串在这里
        - 作为本地空间自动被回收
    - 如果要构造一个字符串 ——> 数组
    - 如果要处理一个字符串 ——> 指针

- char* 是字符串？

  - 字符串可以表达为char*的形式

  - char*不一定是字符串
    - 本意是指字符的指针，可以指向的是字符的数组（就像int*一样）
    - 只有它所指的字符数组有结尾的0，才能说它所指的是字符串

#### 总结（字符串）

- C语言的字符串是以字符数组的形态存在的
  - 不能用运算符对字符串做运算
  - 通过数组的方式可以遍历字符串
- 唯一特殊的地方是字符串字面量可以用来初始化字符数组
- 以及标准库提供了一系列字符串函数

#### 字符串输入输出

- 字符串赋值

  ```c
  char *t = "title";
  char *s;
  s = t;
  ```

  - 并没有产生新的字符串，只是让指针s指向了t所指的字符串，对s的任何操作就是对t做的

- 字符串输入输出

  - char string[8];
  - scanf("%s", string);
  - printf("%s", string);
  - scanf读入一个单词（到空格、tab或回车为止）
  - scanf是不安全的，因为不知道要读入的内容的长度

- 安全的输出

  - char string[n+1];
  - scanf("%ns", string);
    - 在%和s之间的数字表示最多允许读入的字符的数量，这个数字应该比数组的大小小一

- 常见错误

  - char *string;
  - scanf("%S", string);
    - 以为char*是字符串类型，定义了一个字符串类型的变量string就可以直接使用了
      - 由于没有对string初始化为0，所以不一定每次运行都出错

- 空字符串

  - char buffer[100] = "";
    - 这是一个空的字符串，buffer[0] == '\0'
  - char buffer[] = "";
    - 这个数组的长度只有1！

#### 字符串数组

- char **a
  - a是一个指针，指向另一个指针，那个指针指向一个字符（串）
- char a[]\[]
  -  二维数组第二个[]中必须有字符的长度
- char *a[]
  - 字符串数组
- 程序参数
  - int main(int argc, char const *argv[])
  - argv[0]是命令本身
    - 当使用Unix的符号链接时，反映符号链接的名字



## 字符串函数

#### 单字符输入输出

- putchar

  - int putchar(int c);
  - 向标准输出写一个字符
  - 返回写了几个字符，EOF (-1) 表示写失败

- getchar

  - int getchar(void);
  - 向标准输入读入一个字符
  - 返回类型是int是为了返回EOF (-1) 
    - Windows ——> Ctrl-Z
    - Unix ——> Ctrl-D

#### 函数

- string.h

  - strlen

    - size_t strlen(const char *s);
    - 返回s的字符串长度（不包括结尾的0）

  - strcmp

    - int strcmp(const char *s1, const char *s2);
    - 比较两个字符串，返回
      - 0: s1 == s2
      - 1: s1 > s2
      - -1: s1 < s2

  - strcpy

    - char * strcpy(char *restrict dst, const char *restrict src);

    - 把src的字符串拷贝到dst的空间中

      - restrict表明src和dst不重叠（C99）

    - 返回dst

      - 为了能链起代码来

    - 复制一个字符串

      ```c
      char *dst = (char*)malloc(strlen(src)+1);
      strcpy(dst, src);
      ```

  - strcat

    - char * strcat(char *restrict s1, const char *restrict s2);
    - 把s2拷贝到s1的后面，接成一个长的字符串
    - 返回s1
    - s1必须具有足够的空间

  - strchr：字符串中找字符

    - char * strchr(const char *s, int c);
      - 在字符串中找c第一次出现的位置
      - 返回的是指针
    - char * strrchr(const char *s, int c);
      - 从右边找
    - 返回NULL表示没有找到

  - strstr：字符串中找字符串

    - char * strstr(const char *s1, const char *s2);
      - 在字符串中寻找一个字符串
    - char * strcasestr(const char *s1, const char *s2);
      - 在寻找的过程中忽略大小写

  - 安全问题

    - strcpy和strcat都可能出现安全问题
      - 如果目的地没有足够的空间？
    - 安全版本（size_t n：个数）
      - char * strncpy(char *restrict dst, const char *restrict src, size_t n);
      - char * strncat(char *restrict s1, const char *restrict s2, size_t n);
      - int strncmp(cosnt char *s2, const char *s2, size_t n);



## ACLLIB（扩展）

#### ACLLib

- ACLLib
  - 是一个基于Win32API的函数库，提供了相对较为简单的方式来做Windows程序
  - 实际提供了一个.c和两个.h，可以在MSVC和Dev C++（MinGW）中使用
  - 以GPL的方式来源放在github上
  - 纯教学用途，但是编辑模型和思想可以借鉴

#### Win32API

- Windows API（Win32API）

  - 从第一个32位的Windows开始就出现了，就叫做Win32API

  - 它是一个纯C的函数库，就和C标准库一样，使你可以写Windows应用程序

  - 过去很多Windows程序是用这个方式做出了的

  - main()

    - main()成为C语言的入口函数其实和C语言本身无关，你的代码是被一小段叫做启动代码的程序所调用的，它需要一个叫做main的地方
    - 操作系统吧你的可执行程序装载到内存里，启动运行，然后调用你的main函数

  - WinMain()：Windows的应用程序是要用WinMain()来做入口函数

    - As main() is the entry function of an ordinary C Program,WinMain() is the one in Win32API program.

    - Windows applications have a different "startup" code that needs a function "WInMain()"

    - ```c
      #include <windows.h>
      int WINAPI WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, LPSTR lpCmdLine, int nCmdShow)
      {
          MessageBox(NULL, "Goodbye, cruel world!", "Note", MB_OK);
          return 0;
      }
      ```

- ?

  - 如何产生一个窗口？
    - 填充“窗口结构”
  - 如何在窗口中画东西？
    - DC叫做设备上下文，又被叫做设备无关上下文
  - 如何获得用户的鼠标和键盘动作？
    - 消息循环和消息处理代码
  - 如何画出标准的界面：菜单、按钮、输入框
    - acllib目前不能做

#### ACLlib函数

- 创建图形窗口

  - ```c
    void initWindow(const char *name, int left, int top, int width, int height);
    int Setup()
    {
        initWindow("Hello World", 100, 100, 200, 200);
        rturn 0;
    }
    ```

- 坐标系

  - 在Windows中，坐标是以像素点的数字来定义的。对于你创建出来的窗口，左上角是(0,0)，x轴自左向右增长，而y轴自上向下增长

- 终端窗口

  - 如果需要用scanf和printf，则需要首先
    - initConsole();
  - 然后就可以在那个窗口上使用scanf和printf了

- 启动/结束绘图

  - void beginPaint();
  - void endPaint();
  - 任何绘图函数的调用必须在这一对函数调用之间

- 点

  - void putPixel(int x, int y, ACL_Color color);
  - ACL_Color getPixel(int x, int y);
  - 颜色：color
    - RGB(r,g,b)
    - RED,GREEN,BLUE,...

- 线

  - void moveTo(int x, int y);
  - void moveRel(int dx, int dy);
  - void line(int x0, int y0, int xl, intyl);
  - void lineTo(int x, int y);
  - void lineRel(int dx, int dy);
  - void arc(int nLeftRect, int nTopRect, int nRightTrct, int nBottomRect, int nXStartArc, int nYStartArc, int nXEndArc, int nYEndArc)
  - 画笔
    - void setPenColor(ACL_Color color);
    - void setPenWidth(int width);
    - void setPenStytle(ACL_Pen_Style style);
      - PEN_STYLE_SOLID,  实现
      - PEN_STYLE_DASH,  划线 /* ------- */
      - PEN_STYLE_DOT,  点线 /* ....... */
      - PEN_STYLE_DASHDOT,  /* \_.\_.\_._ */
      - PEN_STYLE_DASHDOTDOT,  /* \_..\_..\_.._ */
      - PEN_STYLE_NULL  画一条看不见的线

- 面

  - void chrod(int nLeftRect, int nTopRect, int nRightTrct, int nBottomRect, int nxRadiall, int nYRadiall, int nXRadial2, int nYRadial2);
    - 扇形
  - void elliipse(int nLeftRect, int nTopRect, int nRightTrct, int nBottomRect);
    - 椭圆
  - void pie(int nLeftRect, int nTopRect, int nRightTrct, int nBottomRect, int nxRadiall, int nYRadiall, int nXRadial2, int nYRadial2);
    - 饼
  - void rectanfle(int nLeftRect, int nTopRect, int nRightTrct, int nBottomRect);
    - 矩形
  - void roundrect(int nLeftRect, int nTopRect, int nRightTrct, int nBottomRect, int nWidth, int nHeight);
    - 圆角矩形
  - 刷子
    - 画笔负责线及面的边缘，刷子负责面的内部
    - void setBrushColor(ACL_Color color);
    - void setBrushStyle(ACL_Brush_Stytle stytle);
      - BRUSH_STYLE_SOLIDD = -1,
      - BRUSH_STYLE_HORIZONTAL,  /* ----- */
      - BRUSH_STYLE_VERTICAL,  /* ||||| */
      - BRUSH_STYLE_FDIAGONAL,  /* \\\\\\\\\ */
      - BRUSH_STYLE_BDIAGONA,  /* ///// */
      - BRUSH_STYLE_CROSS,  /* +++++ */
      - BRUSH_STYLE_DIAGCROSS,  /* XXXXX */

- 文字

  - void setTextColor(ACL_Color color);
    - 文字颜色
  - void setTextBkColor(ACL_Color color);
    - 文字背景颜色
  - void setTextSize(int size);
    - 大小
  - void setTextFount(char *pFountName);
    - 字体名字
  - void paintText(int x, int y, const char *pStr);



## 结构类型

#### 枚举

- 枚举是一种用户定义的数据类型，它用关键字`enum`以如下语法来声明
  - `enum 枚举类型名字 {名字0, ..., 名字n};`
- 枚举类型的名字通常并不真的使用，要用的是在大括号里的名字，因为它们就是常量符号，它们的类型是int，值则依次从0到n。如：
  - `enum colors {red,yello,green}`
- 就创建了三个常量，red的值是0，yellow是1，而green是2。
- 当需要一些可以排列起来的常量值是，定义枚举的意义就是给了这些常量值名字
- 枚举量可以作为值
- 枚举类型可以跟上enum作为类型
- 但是实际上是以整数来做内部计算和外部输入输出的
- 套路：自动计数的枚举
  - `enum COLOR {RED, YELLO, GREEN, NumCOLORS};`
  - 这样需要遍历所有的枚举量或者需要建立一个用枚举量做下标的数组的时候就很方便了
- 枚举量
  - 声明枚举量的时候可以指定值
    - enum COLOR {RED=1, YELLO, GREEN=5};
- 枚举只是int
  - 即使给枚举类型的变量赋不存在的整数值也没有任何warning或error
  - 虽然枚举类型可以当做类型使用，但是实际上很(bu)少(hao)用
  - 如果有意义上排比的名字，用枚举比用 const int 方便
  - 枚举比宏（macro）号，因为枚举有int类型
-  在现实中人们用C语言的枚举的主要目的是定义符号量，而不是作为枚举类型使用

#### 结构

- 声明结构类型

  - ```c
    struct date {
        int month;
        int day;
        int year;
    };
    ```

- 和本地变量一样，在函数内部声明的结构类型只能在函数内部使用

- 所以通常在函数外部声明结构类型，这样就可以被多个函数所使用了

- 声明结构的形式

  - ```c
    struct point {
        int x;
        int y;
    };
    struct point p1,p2;  // p1和p2都是point，里面有x和y的值
    ```

  - ```c
    struct {
        int x;
        int y;
    } p1,p2;
    // p1和p2都是一种无名结构，里面有x和y
    ```

  - ```c
    struct point {
        int x;
        int y;
    } p1,p2;
    // p1和p2都是point，里面有x和y的值t
    ```

  - 对于第一和第三种形式，都声明了结构point。但是第二种形式没有声明point，只是定义了两个变量

- 结构变量

  - 定义结构变量

    - ```c
      struct date today;
      today.month=07;
      today.day=31;
      today.year=2014;
      ```

  - 结构的初始化

    - `struct date today = {07,31,2014}`
    - `struct date thismonth= {.month=7, .year=2014}`
      - 没有给出的值填`0`；

  - 结构成员

    - 结构和数组有点像
      - 数组用`[]`运算符和下标访问其单元
        - a[0] = 10;
      - 结构用`.`运算符和名字访问其成员
        - today.day

- 结构运算

  - 要访问整个结构，直接用结构变量的名字
  - 对于整个结构，可以做赋值、取地址，也可以传递给函数参数（数组无法做以下两种运算）
    - p1 = (struct point){5,10};  <==>  相当于 p1.x = 5; p1.y = 10;
    - p1 = p2;  <==>  相当于 p1.x = p2.x; p1.y = p1.y;

- 结构指针

  - 和数组不同，结构变量的名字并不是结构变量的地址，必须使用&运算符
    - struct date *pDate = &today;

#### 结构与函数

- 结构作为函数参数

  - `int numberOfDays(struct date d)`
  - 整个结构可以作为参数的值传入函数
  - 这个时候在函数内新建一个结构变量，并复制调用者的结构的值
  - 也可以返回一个结构
  - 这与数组完全不同 

- 输入结构

  - 没有直接的方式可以一次scanf一个结构

  - 如果我们打算写一个函数来读入结构

    ```c
    #include <stdio.h>
    
    struct point {
        int x;
        int y;
    };
    
    void getStruct(struct point);
    void output(struct point);
    void main() {
        struct point y = {0,0};
        getStruct(y);
        output(y);
    }
    
    void getStruct(struct point p) {
        scanf("%d", &p.x);
        scanf("%d", &p.y);
        printf("%d, %d", p.x, p.y);
    }
    
    void output(struct point p) {
        printf("%d, %d", p.x, p.y);
    }
    ```

  - 但是读入的结构如何传回来呢？

  - 记住C在函数调用时是传值的

    - 所以函数中的p与main中的y是不同的
    - 在函数读入了p的数值之后，没有任何东西回到main，所以y还是{0,0}

  - 解决的方案一

    - 之前的方案，把一个结构传入了函数，然后在函数中操作，但是没有返回回去

      - 问题在于传入函数的是外面那个结构的克隆体，而不是指针
        - 传入结构和传入数组是不同的

    - 在这个输入函数中，完全可以创建一个临时的结构变量，然后把这个结构返回给调用者

      ```c
      #include <stdio.h>
      
      struct point {
          int x;
          int y;
      };
      
      struct point getStruct(void);
      void output(struct point);
      
      int main(int argc, charr const *argv[])
      {
          struct point y = {0,0};
          y = getStruct();
          output(y);
      }
      
      struct point getStruct(void)
      {
          struct point p;
          scanf("%d", &p.x);
          scanf("%d", &p.y);
          printf("%d, %d", p.x, p.y);
          return p;
      }
      
      void output(struct point p) {
          printf("%d, %d", p.x, p.y);
      }
      ```

- 结构指针作为参数

  - K&R 说过（131页）
    - "If a large structure is to be passed to a funcation,it is generally more efficient to pass a pointer than to  copy the whole structure"

- 指向结构的指针

  - 用`->` 表示指针所指的节骨变量中的成员

    ```c
    struct date {
        int month;
        int day;
        int year;
    } myday;
    
    struct date *p = &myday;
    
    (*p).month = 12;
    p->month = 12;
    ```

  - 解决方案二

    ```c
    #include <stdio.h>
    
    struct point {
        int x;
        int y;
    };
    
    struct point* getStruct(struct point*);
    void output(struct point);
    void print(const struct point *p);
    
    int main(int argc, charr const *argv[])
    {
        struct point y = {0,0};
        getStruct(&y);
        output(y);
        output(*getStruct(&Y));
        print(getStruct(&y));
        // getStruct(&y)->x = 0;
        // *getStruct(&y) = (struct point){1,2};
    }
    
    struct point* getStruct(struct point *p)
    {
       
        scanf("%d", &p->x);
        scanf("%d", &p->y);
        printf("%d, %d", p->x, p->y);
        return p;
    }
    
    void output(struct point p) {
        printf("%d, %d", p.x, p.y);
    }
    
    void print(const struct point *p)
    {
        printf("%d, %d", p->x, p->y);
    }
    ```

#### 结构中的结构

- 结构数组

  - struct date dates[100];
  - struct date dates[] = {{4,5,2005},{2,4,2005}};

- 结构中的结构

  ```c
  struct dateAndTime {
      struct date sdate;
      struct time stime;
  };
  ```

- 嵌套的结构

  ```c
  struct point {
      int x;
      int y;
  };
  struct rectangle {
      struct point pt1;
      struct point pt2;
  };
  如果有变量
  	struct rectangle r;
  就可以有：
  	r.pt1.x, r.pt1.y
  	r.pt2.x, r.pt2.y
  如果有变量定义：
  	struct rectangle r, *rp;
  	rp = &r;
  那么下面四种形式是等价的：
  	r.pt1.x
  	rp->pt1.x
  	(r.pt1).x
  	(rp->pt1).x
  但是没有 rp->pt1->x（因为pt1不是指针）
  ```

- 结构中的结构的数组

  ```c
  #include <stdio.h>
  
  struct point {
      int x;
      int y;
  };
  
  struct rectangle {
      struct point p1;
      struct point p2;
  };
  
  void printRect(struct rectangle r)
  {
      printf("<%d, %d> to <%d, %d>\n", r.p1.x, r.p1.y, r.p2.x r.p2.y);
  }
  
  int main(int argc, char const *argv[])
  {
      int i;
      struct rectangle tects[] = {
          {{1, 2}, {3, 4}},
          {{5, 6}, {7, 8}}
      };  // 2 rectangles
      for (i=0;i<2;i++) {
          printRect(rects[i]);
      }
  }
  ```

#### 类型定义

- 自定义数据类型（typedef）

  - C语言提供了一个叫做`typedef`的功能来声明一个已有的数据类型的新名字。比如：

    - typedef int length;

      使得`Length`称为`int`类型的别名

    - 这样，Length这个名字就可以代替int出现在变量定义和参数声明的地方了：

      Length a,b,len;

      Length numbers[10];

  - typedef语法

    - typedef 旧类型 新名字

    ![tyo](typedef.png)

    - ```c
      typedef struct ADate {
          int month;
          int day;
          int year;
      } Date;
      ```

    - ```c
      typedef struct {
          int month;
          int day;
          int year;
      } Date;
      ```

#### 联合（union）

- 语法

  - ```c
    union AnElt {
        int i;
        char c;
    } elt, elt2;
    elt1.i = 4;
    elt2.c = 'a';
    elt2.i = 0xDEADBEEF;
    ```

- 存储

  - 所有的成员占共享一个空间
  - 同一时间只有一个成员是有效的
  - union的大小是其最大的成员
  - sizeof(union ...) = sizeof(每个成员)的最大值

- 初始化

  - 对第一个成员做初始化

- 得到一个类型内部的字节



## 程序结构

#### 全局变量

- 定义在函数外面的变量是全局变量
- 全局变量具有全局的生存期和作用域
  - 它们与任何函数都无关
  - 在任何函数内部都可以使用它们

##### `__func__`：

```c
int main () 
{
    printf("in %s", __func__)  // 当前函数的名字,也就是 main
    return 0;
}
```

- 全局变量初始化
  - 没有做初始化的全局变量会得到0值
    - 指针会得到NULL值
  - 只能用编译时刻已知的值来初始化全局变量
  - 它们的初始化发生在main函数之前
- 被隐藏的全局变量
  - 如果函数内部存在与全局变量同名的变量，则全局变量被隐藏

#### 静态本地变量

- 在本地变量定义时加上`static`修饰符就成为静态本地变量
- 当函数离开的时候，静态本地变量会继续存在并保持其值
- 静态本地变量的初始化只会在第一次进入这个函数时做，以后进入函数时会保持上次离开时的值
- 静态本地变量实际上是特殊的全局变量
- 静态本地变量和全局变量位于相同的内存区域
- 静态本地变量具有全局的生存期，函数内的局部作用域
  - static在这里的意思是局部作用域（本地可访问）

#### 全局变量贴士

- *返回指针的函数
  - 返回本地变量的地址是危险的
  - 返回全局变量或静态本地变量的地址是安全的
  - 返回在函数内malloc的内存是安全的，但是容易造成问题
  - 最好的做法是返回传入的指针
- tips（贴士）
  - 不要使用全局变量来在函数间传递参数和结果
  - 尽量避免使用全局变量
  - *使用全局变量和静态本地变量的函数是线程不安全的

#### 编译预处理和宏

- 编译预处理指令
  - `#`开头的是编译预处理指令
  - 它们不是C语言的成分，但是C语言程序离不开它们
- 其他的编译预处理指令
  - 条件编译
  - error
  - ...
- 编译预处理过程
  - .c -> .i(中间结果文件) -> .s(汇编代码文件) -> .o(目标代码文件) -> a.out

- 宏定义
  - #define用来定义一个宏
  - #define
    - #define <名字> <值>
    - 注意没有结尾的分号，因为不是C的语句
    - 名字必须是一个单词，值可以是各种东西
    - 在C语言的编译器开始编译之前，编译预处理程序（cpp）会把程序中的名字换成值
      - 完全的文本替换
    - gcc保留编译过程中的临时文件指令
      - `gcc --save-temps`
- 宏
  - 如果一个宏的值中有其他的宏的名字，也会被替换的
  - 如果一个宏的值超过一行，最后一行之前的行末需要加`\`
  - 宏的值后面出现的注释不会当作宏的值的一部分
- 没有值的宏
  - #define _DEBUG
  - 这类宏是用于条件编译的，后面有其他的编译预处理指令来检查这个宏是否已经被定义过了
- 预定义的宏
  - `__LINE__`：这个源代码文件的行号，当前所在行的行号； %d
  - `__FILE__`：这个源代码文件的文件名； %s
  - `__DATE__`：编译时候的日期； %s
  - `__TIME__`：编译时候的时间； %s
  - `__STDC__`：当要求程序严格遵循ANSIC标准时该标识符被赋值为1
- 带参数的宏（像函数的宏）
  - #define cube(x) ((x)\*(x)*(x))
  - 宏可以带参数
  - 可以带多个参数
    - #define MIN(a,b) ((a)>(b)?(b):(a))
  - 也可以组合（嵌套）使用其他宏
  - 在大型程序的代码中使用非常普遍
  - 可以非常复杂，如“产生”函数
    - 在#和##这两个运算符的帮助下
      - #的作用就是将#后面的宏参数进行字符串的操作，也就是将#后面的参数两边加上一对双引号使其成为字符串
      - ##的作用就是把2个宏参数连接为1个数
  - 存在中西方文化差异
  - 部分宏会被inline函数替代
- 错误定义的宏
  - #define RADTODEG(x) (x * 57.29578)
  - #define RADTODEG(x) (x) * 57.29578
- 带参数的宏的原则
  - 一切都要有括号
    - 整个值要括号
    - 参数出现的每个地方都要括号
  - #define RADTODEG(x) ((x) * 57.29578)
- 分号
  - 定义宏的时候结尾不要加`;` 

#### 大程序结构

- 多个.c文件
  - main()里的代码太长了适合分成几个函数
  - 一个源代码文件太长了适合分成几个文件
  - 两个独立的源代码文件不能编译形成可执行的程序
- 项目
  - 在Dev C++中新建一个项目，然后把几个源代码文件加入进去
  - 对于项目，Dev C++的编译会把一个项目中所有的源代码文件都编译后，链接起来
  - 有的IDE有分开的编译和构建两个按钮，前者是对单个源代码文件编译，后者是对整个项目做链接
- 编译单元
  - 一个.c文件是一个编译单元
  - 编译器每次编译只处理一个编译单元
- 头文件
  - 把函数原型放到一个头文件（以.h结尾）中，在需要调用这个函数的源代码文件（.c文件）中#include这个头文件，就能让编译器在编译的时候知道函数的原型
  - 在使用和定义这个函数的地方都应该#include这个头文件
  - 一般的做法就是任何.c都有对应的同名的.h，把所有对外公开的函数的原型和全局变量的声明都放进去
- #include
  - #include是一个编译预处理指令，和宏一样，在编译之前就处理了
  - 它把那个文件的全部文本内容原封不动地插入到它所在的地方
  - 所以也不是一定要在.c文件的最前面#include
- ""还是<>
  - #include有两种形式来指出要插入的文件
    - ""要求编译器首先在当前目录（.c文件所在的目录）寻找这个文件，如果没有，到编译器指定的目录去找
    - <>让编译器只在指定的目录去找
  - 编译器自己知道自己的标准库的头文件在哪里
  - 环境变量和编译器命令行参数也可以指定寻找头文件的目录
- #include的误区
  - #include不是用来引入库的
  - stdio.h里只有printf的原型，printf的代码在另外的地方，某个.lib(Windows)或.a(Unix)中
  - 现在的C语言编译器默认会引入所有的标准库
  - #include <stdio.h>只是为了让编译器知道printf函数的原型，保证你调用时给出的参数值是正确的
- 不对外公开的函数
  - 在函数前面加上static就使得它成为只能在所在的编译单元中被使用的函数
  - 在全局变量前面加上static就使得它成为只能在所在的编译单元中被使用的全局变量

#### 声明

- 变量的声明

  - int i; 是变量的定义
  - extern int i; 是变量的声明

- 声明和定义

  - 声明是不产生代码的东西
    - 函数原型
    - 变量声明
    - 结构声明
    - 宏声明
    - 枚举声明
    - 类型声明
    - inline函数
  - 定义是产生代码的东西
    - 函数
    - 全局变量

- 头文件

  - 只有声明可以被放在头文件中
    - 是规则不是法律
  - 否则会造成一个项目中多个编译单元里有重名的实体
    - *某些编译器允许几个编译单元中存在同名的函数，或者用weeak修饰符来强调这种存在

- 重复声明

  - 同一个编译单元里，同名的结构不能被重复声明
  - 如果你的头文件里有结构的声明，很难这个头文件不会在一个编译单元里被#include多次
  - 所以需要“标准头文件结构”

- 标准头文件结构

  - 运用条件编译和宏，保证这个头文件在一个编译单元中只会被#include一次

  - #pragma once也能起到相同的作用，但是不是所有的编译器都支持

    ```C
    #ifndef __LIST_HEAD__
    #define __LIST_HEAD__
    ...
    #endif
    ```



## 文件

#### 文件

- 格式化的输入输出

  - printf

    - %[flags]\[width]\[.prec][hlL]type

    - [flags]

      |  Flag   |     含义      |
      | :-----: | :-----------: |
      |    -    |    左对齐     |
      |    +    | 前面放 + 或 - |
      | (space) |   整数留空    |
      |    0    |     0填充     |

    - [width]\[.prec]

      | width 或 prec |            含义            |
      | :-----------: | :------------------------: |
      |    number     |         最小字符数         |
      |       *       |     下一个参数是字符数     |
      |    .number    |       小数点后的位数       |
      |      .*       | 下一个参数是小数点后的位数 |

    - [hlL]

      | 类型修饰 |    含义     |
      | :------: | :---------: |
      |    hh    |  单个字节   |
      |    h     |    short    |
      |    l     |    long     |
      |    ll    |  long long  |
      |    L     | long double |

    - 类型

      |  type  |        用于        | type |      用于       |
      | :----: | :----------------: | :--: | :-------------: |
      | i 或 d |        int         |  g   |      float      |
      |   u    |    unsigned int    |  G   |      float      |
      |   o    |       八进制       | a或A |  十六进制浮点   |
      |   x    |      十六进制      |  c   |      char       |
      |   X    | 字母大写的十六进制 |  s   |     字符串      |
      | f 或 F |      float,6       |  p   |      指针       |
      | e 或 E |        指数        |  n   | 读入/写入的个数 |

  - scanf

    - %[flag]type

      | flag |    含义    | flag |    含义     |
      | :--: | :--------: | :--: | :---------: |
      |  *   |    跳过    |  l   | long,double |
      | 数字 | 最大字符数 |  ll  |  long long  |
      |  hh  |    char    |  L   | long double |
      |  h   |   short    |      |             |

    - 类型

      |  type   |             用于             | type  |      用于      |
      | :-----: | :--------------------------: | :---: | :------------: |
      |    d    |             int              |   s   | 字符串（单词） |
      |    i    | 整数，可能为十六进制或八进制 | [...] |  所允许的字符  |
      |    u    |         unsigned int         |   p   |      指针      |
      |    o    |            八进制            |   x   |    十六进制    |
      | a,e,f,g |            float             |   c   |      char      |

  - printf和scanf的返回值

    - 读入的项目数
    - 输出的字符数
    - 在要求严格的程序中，应该判断每次调用scanf或printf的返回值，从而了解程序运行中是否存在问题

#### 文件输入输出

- 用`>`和`<`做重定向

- FILE

  - FILE* fopen(const char * restrict path, const char * restrict mode);
  - int fclose(FILE *stream);
  - fscanf(FILE*, ...)
  - fprintf(FILE*, ...)

- 打开文件的标准代码

  ```c
  FILE* fp = fopen("file", "r");
  if ( fp ) {
      fscanf(fp, ...);
      fcolse)fp, ...
  } else {
      ...
  }
  ```

- fopen

  |  r   |                      打开只读                      |
  | :--: | :------------------------------------------------: |
  |  r+  |               打开读写，从头文件开始               |
  |  w   |     打开只写。如果不存在则新建，如果存在则清空     |
  |  w+  |     打开读写。如果不存在则新建，如果存在则清空     |
  |  a   | 打开追加。如果不存在则新建，如果存在则从文件尾开始 |
  | ..x  |          只新建，如果文件已存在则不能打开          |

#### 二进制文件

- 二进制文件
  - 其实所有的文件最终都是二进制的
  - 文本文件无非是用最简单的方式可以读写的文件
    - more、tail
    - cat
    - vi
  - 而二进制文件是需要专门的程序来读写的文件
  - 文本文件的输入输出是格式化，可能经过转码
- 文本 VS 二进制
  - Unix喜欢用文本文件来做数据存储和程序配置
    - 交互式终端的出现使得人们喜欢用文本和计算机“talk”
    - Unix的shell提供了一些读写文本的小程序
  - Windows喜欢用二进制文件
    - DOS是草根文化，并不继承和熟悉Unix文化
    - PC刚开始的时候能力有限，DOS的能力更有限，二进制更接近底层
  - 文本的优势是方便人类读写，而且跨平台
  - 文本的缺点是程序输入输出要经过格式化，开销大
  - 二进制的缺点是人类读写困难，而且不跨平台
    - int的大小不一致，大小端的问题...
  - 二进制的优点是程序读写快
- 程序为什么要文件
  - 配置
    - Unix用文本，Windows用注册表
  - 数据
    - 稍微有点量的数据都放数据库了
  - 媒体
    - 这个只能是二进制的
  - 现实是，程序通过第三方库来读写文件，很少直接读写二进制文件了

#### 二进制读写

- size_t fread(void *restrict ptr, size_t size, size_t nitems, FILE *restrict stream);
  - void *restrict ptr：要读的内存
  - size_t size：这块内存有多大
  - size_t nitems：有几个这样的内存
  - FILE *restrict stream：文件指针
- suze_t fwirte(const void *restrict ptr, size_t size, size_t nitems, FILE *restrict stream);
  - const void *restrict ptr：要读的内存
  - size_t size：这块内存有多大
  - size_t nitems：有几个这样的内存
  - FILE *restrict stream：文件指针
- 注意FILE指针最后一个参数，返回的是成功读写的字节数
- nitem
  - 因为二进制文件的读写一般都是通过对一个结构变量的操作来进行的
  - 于是nitem就是用来说明这次读写几个结构变量
- sprintf：输出为字符串

#### 在文件中定位

- long ftell(FILE *stream);
  - 得到现在所在的位置
- int fseek(FILE *stream, long offset, int whence);
  - FILE *stream：文件
  - long offset：位置
  - int whence：
    - SEEK_SET：从头开始
    - SEEK_CUR：从当前位置开始
    - SEEK_END：从尾开始（倒过来）

#### 可移植性

- 这样的二进制文件不具有可移植性
  - 在int为32位的机器上写成的数据文件无法直接在int为64位的机器上正确读出
- 解决方案之一是放弃使用int，而是typedef具有明确大小的类型
- 更好的方案是用文本



## *位运算

#### 按位运算

- C有这些按位运算的运算符：

  - `&`：按位的与
    - 两个数的二进制每一位做运算，只有同一位都是1的时候为1，否则为0
      - 如果 (x)~i~ == 1 并且 (y)~i~ == 1，那么 (x & y)~i~ = 1
      - 否则的话 (x & y)~i~ = 0
    - 按位与常用于两种应用：
      - 让某一位或某些位为0：x & 0xFE
        - FE：11111110
          - 是一个数的最低位变成0
      - 取一个数中的一段：xx & 0xFF
        - FF：与FF同位的那段保留
  - `|`：按位的或
    - 两个数对应位上有一个是1结果就是1，否则是0
      - 如果 (x)~i~ == 1 或 (y)~i~ == 1，那么 (x | y)~i~ = 1
      - 否则的话 (x | y)~i~ = 0
    -  按位或常用于两种应用：
      - 使得一位或几位为1：x | 0x01
      - 把两个数拼起来：0x00FF | 0xFF00
  - `~`：按位取反
    - 把数的每一个bytes，从1变为0，0变为1
      - (\~x)~i~ = 1 - (x)~i~
    - 想得到全部位为1的数：~0
  - `^`：按位的异或
    - 如果两个位相等结果为0，如果两个位不相等结果为1
      - 如果 (x)~i~ == (y)~i~，那么 (x ^ y)~i~ = 0
      - 否则的话 (x ^ y)~i~ = 1
    - 如果x和y相等，那么 x ^ y 的结果为0
    - 对一个变量用同一个值异或两次，等于什么也没做
      - x ^ y ^ y --> x

  ##### 移位运算

  - `<<`：左移
    - i << j
      - i中所有的位向左移动j个位置，而右边填入0
      - 所有小于int的类型，移位以int的方式来做，结果是int
      - x <<= 1 等价于 x *= 2
      - x <<= n 等价于 x *= 2^n^
  - `>>`：右移
    - i >> j
      - i中所有的位向右移j位
      - 所有小于int的类型，移位以int的方式来做，结果是int
      - 对于unsigned的类型，左边填入0
      - 对于signed的类型，左边填入原来的最高位（保持符号不变）
      - x >>= 1 等价于 x /= 2
      - x >>= n 等价于 x /= 2^n^
  - 移位的位数不要用复数，这是没有定义的行为
    - x << -2  // !!NO!!

#### 逻辑运算 VS 按位运算

- 对于逻辑运算，它只看到两个值：0和1
- 可以认为逻辑运算相当于把所有非0值都变成1，然后做按位运算
  - 5 & 4 --> 4 而 5 && 4 --> 1 & 1 --> 1
  - 5 | 4 --> 4 而 5 || 4 --> 1 | 1 --> 1
  - ~4 --> 3 而 !4 --> !1 --> 0

#### 位运算例子

- 输出一个数的二进制

  ```c
  #include <stdio.h>
  
  int main(int argc, char const *argv[])
  {
      int number;
      scanf("%d", &number);
      unsigned mask = 1u<<31;  // unsigned直接加变量名的时候，编译器默认是int
      for ( ; mask ; mask >>= 1 ) {
          printf("%d", number & mask?1:0);
      }
      printf("\n");
      
      return 0;
  }
  ```

#### 位段

- 把一个int的若干位组合成一个结构

  ```c
  struct {
      unsigned int leading : 3;  // : 后的数字是这个成员占几个bit
      unsigned int FLAG1 : 1;
      unsigned int FLAG2 : 1;
      int trailing : 11;
  }
  ```

- 可以直接用位段的成员名称来访问bit

  - 比位移、与、或还方便

- 编译器会安排其中的位的排列，不具有可移植性

- 当所需的位超过一个int时会采用多个int



## *链表

#### 可变数组

- 可变数组

  - Resizable Array

    - Think about a set of functions that provide a mechanism of resizable array of int
      - Growable
      - Get the current size
      - Access to the elements

  - the Interface

    - Array array_create(int init_size);
    - void array_free(Array *a);

    ##### 可变数组的数据访问

    - int array_size(const Array *a);
    - int* array_at(Array *a, int index);

    ##### 可变数组的自动增长

    - void array_inflate(Array *a, int more_size)

#### 链表

- 可变数组的缺陷

  - issues
    - Allocate new memory each time it inflates is an easy and clean way. But
      - It takes time to copy, and
      - may fail in memory restricted situation
  - Linked blocks
    - No copy

- 链表

  - 结点

    ```c
    typedef struct _node {
        int value;
        struct _node *next;
    } Node;
    ```

- 链表的函数

- 链表的搜索

- 链表的删除

  - How do we find the boundary?

    ```c
    for ( q=0,p = head; p; q=p,p=p->next ) {
        if ( p->value == i ) {
            q->next = p->next;
        }
    }
    ```

    - Any pointer at the left of -> must be checked

- 链表的清除