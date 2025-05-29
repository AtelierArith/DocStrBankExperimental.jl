```
deflate(f::MPolyRingElem{T}, defl::Vector{Int}) where T <: RingElement
```

同じ係数を持つ多項式を返しますが、指数は最大限に縮小されます。つまり、$f$のその変数のすべての指数の次数を割り切る最大の整数で各指数を割ります。
