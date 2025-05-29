```
xnor(a, b)
xnor(a, b, c...)
```

Bitwise xnor. When n>2 operands are provided, xnor is left-associative (that is, `xnor(a, b, c) = reduce(xnor, [a,b,c])`.
