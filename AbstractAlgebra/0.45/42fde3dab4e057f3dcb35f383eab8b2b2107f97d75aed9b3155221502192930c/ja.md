```
vars(a::FracElem{S}) where {S <: MPolyRingElem{<: RingElement}}
```

$ a $ に実際に現れる変数を返します。返される変数は `base_ring(a)` の要素です。分子の変数が最初に来ます。
