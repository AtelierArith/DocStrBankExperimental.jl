```
Overlaps{T} <: DE9IMPredicate{T}
Overlaps() = Overlaps(nothing)
```

`Overlaps`: 幾何学Aは幾何学Bと重なっているのは、両者がいくつかの内部点を共有している場合に限ります。

`Overlaps`述語は、2つの幾何学がいくつかの内部点を共有している場合にtrueを返します。
