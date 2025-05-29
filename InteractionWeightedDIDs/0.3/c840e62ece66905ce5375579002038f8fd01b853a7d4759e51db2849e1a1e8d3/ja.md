```
AggregatedRegDIDResult{TR,Haslsweights,P<:RegressionBasedDIDResult,I} <: AggregatedDIDResult{TR,P}
```

[`RegressionBasedDIDResult`](@ref) から集約された推定結果。 [`agg`](@ref) も参照してください。

# フィールド

  * `parent::P`: 結果が生成される [`RegressionBasedDIDResult`](@ref)。
  * `inds::I`: 結果を生成するために使用される `parent` からの係数推定のインデックス。
  * `coef::Vector{Float64}`: 係数推定。
  * `vcov::Matrix{Float64}`: 推定値の分散共分散行列。
  * `coefweights::Matrix{Float64}`: `parent` からの係数推定を集約するために使用される係数重み。
  * `treatweights::Vector{Float64}`: 結合された `treatcells` に対する `parent` からの `treatweights` の合計。
  * `treatcounts::Vector{Int}`: 結合された `treatcells` に対する `parent` からの `treatcounts` の合計。
  * `coefnames::Vector{String}`: 係数名。
  * `coefinds::Dict{String, Int}`: 名前によって推定値を取得するための整数インデックスへの `coefnames` からのマップ。
  * `treatcells::VecColumnTable`: `parent` からの `treatcells` から結合されたセル。
  * `lsweights::Union{TableIndexedMatrix, Nothing}`: セルレベルの最小二乗重み。
  * `cellymeans::Union{Vector{Float64}, Nothing}`: 結果変数のセルレベルの平均。
  * `cellweights::Union{Vector{Float64}, Nothing}`: 各セルの総サンプル重み。
  * `cellcounts::Union{Vector{Int}, Nothing}`: 各セルの観測数。
