```
LazyProduct(operators[, factor=1])
LazyProduct(op1, op2...)
```

Lazy evaluation of products of operators.

The factors of the product are stored in the `operators` field. Additionally a complex factor is stored in the `factor` field which allows for fast multiplication with numbers.
