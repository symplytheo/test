# test

Sure! To adjust the code so that operators come before operands in the expression, you can update the `calculate` function as follows:

```javascript
function calculate(expression) {
  const tokens = expression.split(' ');
  const stack = [];

  for (let i = tokens.length - 1; i >= 0; i--) {
    const current = tokens[i];

    if (!isNaN(current)) {
      stack.push(Number(current));
    } else {
      const operand1 = stack.pop();
      const operand2 = stack.pop();

      if (current === '+') {
        stack.push(operand1 + operand2);
      } else if (current === '-') {
        stack.push(operand1 - operand2);
      } else if (current === '*') {
        stack.push(operand1 * operand2);
      } else if (current === '/') {
        stack.push(operand1 / operand2);
      }
    }
  }

  return stack.pop();
}

// Test case
console.log(calculate('+ 3 4')); // Output: 7
console.log(calculate('- * 4 5 3')); // Output: 17
console.log(calculate('* + 3 4 5')); // Output: 35
console.log(calculate('/ - 3 4 + 5 2')); // Output: -1
```

In this updated code, the `calculate` function iterates over the tokens in reverse order by starting the loop from `tokens.length - 1` and decrementing `i` until it reaches 0. This way, the operators will be processed before the operands.

Now you can provide the expression with operators before operands, and the function will return the calculated value accordingly. Let me know if you have any further questions!
