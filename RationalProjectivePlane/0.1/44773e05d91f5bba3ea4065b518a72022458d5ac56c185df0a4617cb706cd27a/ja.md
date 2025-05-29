```
cartesian(p::PPoint)::Vector
```

有限点が与えられた場合、そのカルテジアン座標を返します。すなわち、`p == PPoint(x,y,1)` となる有理数 `x` と `y` です。
