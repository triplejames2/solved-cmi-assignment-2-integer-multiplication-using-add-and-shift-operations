Download Link: https://assignmentchef.com/product/solved-cmi-assignment-2-integer-multiplication-using-add-and-shift-operations
<br>
<strong>Integer Multiplication using Add and Shift Operations</strong>

Create an ARMv8 assembly language program that implements the following integer multiplication program:




#include &lt;stdio.h&gt;

#define FALSE 0

#define TRUE  1




int main()

{

int multiplier, multiplicand, product, i, negative;

long int result, temp1, temp2;




// Initialize variables

multiplicand = -16843010;

multiplier = 70;

product = 0;




// Print out initial values of variables

printf(“multiplier = 0x%08x (%d)  multiplicand = 0x%08x (%d)

”,

multiplier, multiplier, multiplicand, multiplicand);




// Determine if multiplier is negative

negative = multiplier &lt; 0 ? TRUE : FALSE;




// Do repeated add and shift

for (i = 0; i &lt; 32; i++) {

if (multiplier &amp; 0x1) {

product = product + multiplicand;

}




// Arithmetic shift right the combined product and multiplier

multiplier = multiplier &gt;&gt; 1;

if (product &amp; 0x1) {

multiplier = multiplier | 0x80000000;

} else {

multiplier = multiplier &amp; 0x7FFFFFFF;

}

product = product &gt;&gt; 1;

}




// Adjust product register if multiplier is negative

if (negative) {

product = product – multiplicand;

}




// Print out product and multiplier

printf(“product = 0x%08x  multiplier = 0x%08x
”,

product, multiplier);




// Combine product and multiplier together

temp1 = (long int)product &amp; 0xFFFFFFFF;

temp1 = temp1 &lt;&lt; 32;

temp2 = (long int)multiplier &amp; 0xFFFFFFFF;

result = temp1 + temp2;




// Print out 64-bit result

printf(“64-bit result = 0x%016lx (%ld)
”, result, result);




return 0;

}







Be sure to use 32-bit registers for variables declared using <em>int</em>, and 64-bit registers for variables declared using <em>long int</em>. Use <em>m4</em> macros to name the registers to make your code more readable. Name the program <em>assign2a.asm</em>. Optimize your code so that it uses as few instructions as possible.




Also run the program in <em>gdb</em>, displaying the contents of key registers as the program executes; you should show that the algorithm is working as expected. Capture the <em>gdb</em> session using the Unix command <em>script</em> and name the output file <em>script.txt</em>.




Create a second version of the program (called <em>assign2b.asm</em>) that uses 522133279 for the multiplicand, and 200 for the multiplier. Also create a third version of the program (called <em>assign2c.asm</em>) that uses -252645136 for the multiplicand, and -256 for the multiplier.




<strong>Other Requirements </strong>




Make sure your code is properly formatted into columns, is readable and fully documented, and includes identifying information at the top of each file. You must comment each line of assembly code. Your code should also be well designed: make sure it is well organized, clear, and concise.




<strong>New Skills Needed for this Assignment:</strong>




<ul>

 <li>Use of bitwise logical and shift operations</li>

 <li>Use of branching and condition code tests</li>

 <li>Understanding of hexadecimal and binary numbers</li>

</ul>