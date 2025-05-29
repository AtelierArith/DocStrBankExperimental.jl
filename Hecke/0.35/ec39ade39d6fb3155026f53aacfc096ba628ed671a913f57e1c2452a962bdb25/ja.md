```
rational_reconstruction(a::PolyRingElem{S}, b::PolyRingElem{S}, n::Int, m::Int)
```

`true` と $x, y$ を返します。$ay = x \mod b$ かつ $degree(x) \leq n$, $degree(y) \leq m$ となる場合、そうでない場合は `false`（およびガーベッジ）を返します。
