```
==(x::NCPolyRingElem{T}, y::NCPolyRingElem{T}) where T <: NCRingElem
```

$ x == y $ が算術的に等しい場合は `true` を返し、そうでない場合は `false` を返します。異なる精度の冪級数は、2つの精度の最小値に算術的に等しい場合があることを思い出してください。
