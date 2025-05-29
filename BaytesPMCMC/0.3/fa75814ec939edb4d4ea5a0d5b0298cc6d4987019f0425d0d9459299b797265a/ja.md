```julia
struct PMCMCTune{T<:ModelWrappers.Tagged} <: BaytesCore.AbstractTune
```

PMCMC チューニングコンテナ。

# フィールド

  * `tagged::ModelWrappers.Tagged`: タグ付きモデルパラメータ。
