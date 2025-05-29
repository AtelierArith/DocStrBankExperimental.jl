```
==(x::T, y::PolyRingElem{T}) where T <: RingElem = y == x
```

$ x = y $ の場合は `true` を返します。
