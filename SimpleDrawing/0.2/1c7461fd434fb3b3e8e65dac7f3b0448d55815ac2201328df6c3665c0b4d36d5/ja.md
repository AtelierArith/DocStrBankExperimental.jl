```
find_center(a::Complex, b::Complex, c::Complex)::Complex
```

`find_center(a,b,c)`: 複素平面上の3つの点が与えられたとき、すべての点から等距離にある点 `z` を見つけます。3つの点が共線の場合は `Inf + Inf*im` を返します。
