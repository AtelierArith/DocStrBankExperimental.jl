```
rational_reconstruction{S}(a::PolyRingElem{S}, b::PolyRingElem{S})
```

Returns `true` and $x/y$ s.th. $ay = x mod b$ and $degree(x), degree(y) <= degree(b)/2$    or `false` (and garbage) if this is not possible. Shortcut to the more general function.
