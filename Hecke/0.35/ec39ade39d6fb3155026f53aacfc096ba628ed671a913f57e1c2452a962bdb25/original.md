```
rational_reconstruction(a::PolyRingElem{S}, b::PolyRingElem{S}, n::Int, m::Int)
```

Returns `true` and $x, y$ s.th. $ay = x mod b$ and $degree(x) <= n$, $degree(y) <= m$    or `false` (and garbage) if this is not possible.
