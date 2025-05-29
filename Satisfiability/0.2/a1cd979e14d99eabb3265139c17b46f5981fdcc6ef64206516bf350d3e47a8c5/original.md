```
@satvariable(a, Int)
b = int2bv(a, 8)
```

Wrap IntExpr a, representing a conversion to a BitVector of specified length. This operation has high overhead and may impact solver performance.
