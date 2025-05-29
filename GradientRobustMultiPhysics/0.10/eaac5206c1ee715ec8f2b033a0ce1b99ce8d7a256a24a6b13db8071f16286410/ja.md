```julia
struct FEVector{T, Tv, Ti}
```

平坦な配列ですが、関連するFESpaceの係数を持ついくつかのFEVectorBlockのサブディビジョンの追加レイヤーがあります。
