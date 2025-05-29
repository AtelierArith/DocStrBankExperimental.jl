```
fit(::Type{<:Factor}, data, names, fonames, nfac::Integer; kwargs...)
```

`nfac` 個の因子を使用して、`Tables.jl` 互換の `data` テーブルから `names` でインデックス付けされた変数を使用して因子モデルを適合させます。観測された因子は、`data` の列のインデックスとして `fonames` で指定されます。各変数の R 二乗は、平均がゼロで標準偏差が 1 の標準化データに基づいて計算されます。詳細については、[`Factor`](@ref) および [`fit!`](@ref) を参照してください。

# キーワード

  * `subset::Union{BitVector, Nothing}=nothing`: 推定に使用する `data` のサブセット。
  * `TF::Type=Float64`: 推定に使用される数値型。
  * `svdalg::Algorithm=DivideAndConquer()`: 特異値分解のためのアルゴリズム。
  * `maxiter::Integer=10000`: 最大反復回数; モデルが観測因子と未観測因子の両方を含む場合にのみ関連します。
  * `tol::Real=1e-8`: 収束のための許容レベル; モデルが観測因子と未観測因子の両方を含む場合にのみ関連します。

# 参考文献

**Stock, James H. and Mark W. Watson.** 2016. "Chapter 8–-Dynamic Factor Models, Factor-Augmented Vector Autoregressions, and Structural Vector Autoregressions in Macroeconomics." In *Handbook of Macroeconomics*, Vol. 2A, edited by John B. Taylor and Harald Uhlig, 415–525. Amsterdam: Elsevier.
