```
denest(S::MPolyRing, f::Union{PolyRingElem, MPolyRingElem})
```

反復多項式環の要素 `f` をデネストすることによって得られる `S` の要素を返します。環 `S` は `denest(parent(f))` と同じ基底環と変数の数を持つ必要があります。
