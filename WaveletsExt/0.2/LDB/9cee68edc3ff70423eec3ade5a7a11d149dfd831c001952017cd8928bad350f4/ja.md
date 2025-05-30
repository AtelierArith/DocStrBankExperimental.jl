```
change_nfeatures(f, x, n_features)
```

信号から抽出された特徴量の数を `f.n_features` から `n_features` に変更します。

!!! warning 入力の `n_features` が `f.n_features` より大きい場合、特徴量を再選択する前に現在の `f.n_features` に基づいて信号が再生成されます。これにより、追加の特徴量が正確性と効果が低下します。多くの場合、「追加の」特徴量はゼロになる傾向があります。

# 引数

  * `f::LocalDiscriminantBasis`: ローカル判別基底オブジェクト。
  * `x::AbstractMatrix{S} where S<:AbstractFloat`: 元の信号から抽出されたLDB特徴量の行列で、各列は対応する信号から抽出された係数に対応します。
  * `n_features::Integer`: LDBによって選択される特徴量の希望数。

# 戻り値

  * `xₜ::Matrix{S}`: 抽出されたLDB特徴量の行列で、行数は以前の `f.n_features` ではなく、現在は `n_features` になります。

**関連情報:** [`LocalDiscriminantBasis`](@ref), [`fit!`](@ref), [`fit_transform`](@ref),     [`transform`](@ref), [`inverse_transform`](@ref)
