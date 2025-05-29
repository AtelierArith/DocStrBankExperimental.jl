```julia
mutable struct Particles{R, B, I<:Integer} <: BaytesFilters.AbstractParticles
```

伝播のための粒子コンテナを含みます。

# フィールド

  * `val::ElasticArrays.ElasticArray{B, 2, 1, Vector{B}} where B`: 粒子の軌道、軌道の可能な形状についての議論のため。
  * `ancestor::ElasticArrays.ElasticArray{I, 2, 1, Vector{I}} where I<:Integer`: pfにおける再サンプリングステップの保存された祖先。
  * `weights::BaytesCore.ParameterWeights`: 粒子の重み。
  * `buffer::BaytesFilters.ParticleBuffer{B, I, R} where {R, B, I<:Integer}`: 粒子の再サンプリングに必要なバッファ値。
  * `ℓobjective::BaytesCore.Accumulator`: 対数尤度推定。
