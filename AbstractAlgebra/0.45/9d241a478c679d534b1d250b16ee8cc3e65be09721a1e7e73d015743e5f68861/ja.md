```
==(x::MatrixElem{T}, y::MatrixElem{T}) where {T <: NCRingElement}
```

$ x == y $ が算術的に等しい場合は `true` を返し、それ以外の場合は `false` を返します。異なる精度の冪級数は、2つの精度の最小値に算術的に等しい場合があることを思い出してください。
