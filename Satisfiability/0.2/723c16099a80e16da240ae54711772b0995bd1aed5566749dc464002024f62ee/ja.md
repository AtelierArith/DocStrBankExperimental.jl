```
xnor(a, b)
xnor(a, b, c...)
```

ビット単位の xnor。n>2 のオペランドが提供されるとき、xnor は左結合です（つまり、`xnor(a, b, c) = reduce(xnor, [a,b,c])`）。
