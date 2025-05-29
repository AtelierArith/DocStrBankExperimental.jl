```
number_of_coordinates(M::AbstractManifold, B::AbstractBasis)
number_of_coordinates(M::AbstractManifold, ::𝔾)
```

多様体 `M` 上のフィールドタイプ `𝔾` の基底における座標の数を計算します。これは、`B` によって表されるベクトルの数、または [`CachedBasis`](@ref) の場合は `B` に格納されているベクトルの数にも対応します。
