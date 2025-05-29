```
==(x::FracElem{T}, y::FracElem{T}) where {T <: RingElem}
```

$ x == y $ の場合は `true` を返し、そうでなければ `false` を返します。異なる精度の冪級数は、2つの精度の最小値に対して算術的に等しい場合があることを思い出してください。
