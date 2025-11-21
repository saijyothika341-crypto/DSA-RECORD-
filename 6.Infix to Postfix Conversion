
*Aim:*
To convert a given infix expression to a postfix expression using a stack.

*Algorithm:*

1.Initialize an empty stack and empty postfix string.
2.Read the infix expression.
3.For each character in the infix expression:
  1.If it is an operand, append it to the postfix string.
  2.If it is '(', push it to the stack.
  3.If it is ')', pop and append from the stack until '(' is encountered.
  4.If it is an operator, pop and append operators from the stack with higher   or equal precedence, then push the current operator.
4.After scanning all characters, pop and append all remaining operators from the stack.
5.Print the postfix expression.

*Program:*

#include <stdio.h>
#include <ctype.h>
#include <string.h>

#define MAX 100
char stack[MAX];
int top = -1;

// Check empty
int isEmpty() {
    return top == -1;
}

// Push
void push(char item) {
    if (top >= MAX - 1) {
        printf("stack overflow\n");
        return;
    }
    stack[++top] = item;
}

// Pop
char pop() {
    if (isEmpty()) {
        printf("stack underflow\n");
        return -1;
    }
    return stack[top--];
}

// Peek
char peek() {
    if (isEmpty())
        return -1;
    return stack[top];
}

// Operator precedence
int precedence(char item) {
    if (item == '^')
        return 3;
    else if (item == '*' || item == '/')
        return 2;
    else if (item == '+' || item == '-')
        return 1;
    else
        return 0;
}

int main() {
    char infix[MAX], postfix[MAX];
    int i, k = 0;
    char ch, temp;

    // Read infix expression
    printf("Enter in-fix Expression: ");
    scanf("%s", infix);

    // Convert to postfix
    for (i = 0; i < strlen(infix); i++) {
        ch = infix[i];

        if (isalnum(ch)) {                  // operand
            postfix[k++] = ch;
        }
        else if (ch == '(') {               // left bracket
            push(ch);
        }
        else if (ch == ')') {               // right bracket
            while (!isEmpty() && (temp = pop()) != '(')
                postfix[k++] = temp;
        }
        else {                              // operator
            while (!isEmpty() && precedence(peek()) >= precedence(ch))
                postfix[k++] = pop();
            push(ch);
        }
    }

    // Pop remaining operators
    while (!isEmpty())
        postfix[k++] = pop();

    postfix[k] = '\0';

    // Print postfix
    printf("Postfix expression: %s\n", postfix);

    return 0;
}


*Output:*
Enter in-fix Expression: A+B*C
Postfix expression: ABC*+

Enter in-fix Expression: (A+B)*C
Postfix expression: AB+C*

Enter in-fix Expression: A*(B+C)/D
Postfix expression: ABC+*D/

*Result:*
The program To convert a given infix expression to a postfix expression using a stack was successfully implemented, executed, and the output was Verified.
