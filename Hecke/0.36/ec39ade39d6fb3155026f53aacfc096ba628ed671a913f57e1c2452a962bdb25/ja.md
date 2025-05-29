```
rational_reconstruction(a::PolyRingElem{S}, b::PolyRingElem{S}, n::Int, m::Int)
```

`true` と $x, y$ を返します。条件は $ay = x \mod b$ であり、$degree(x) \leq n$, $degree(y) \leq m$ です。そうでない場合は `false`（およびゴミ）を返します。
