```
commutator(k::TBAKind, hilbert::Hilbert{<:Internal}) -> Union{AbstractMatrix, Nothing}
```

自由量子格子系の単一粒子演算子の交換関係をタイトバインディング近似を用いて取得します。
