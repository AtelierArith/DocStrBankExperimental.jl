```
@satvariable(b, BitVector, 8)
a = bv2int(b)
```

Wrap BitVectorExpr b, representing a conversion to IntExpr. The value of the integer expression will be limited by the size of the wrapped BitVector. This operation has high overhead and may impact solver performance.
