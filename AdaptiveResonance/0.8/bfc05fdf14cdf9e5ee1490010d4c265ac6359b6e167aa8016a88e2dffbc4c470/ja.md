```julia
mutable struct opts_FAM <: AdaptiveResonance.ARTOpts
```

# 概要

Fuzzy ARTMAP学習者のオプションを実装します。

これらのオプションは、カスタムオプションのキーワード引数を受け取る[`Parameters.jl`](https://github.com/mauro3/Parameters.jl)構造体です。各フィールドには、以下に示すデフォルト値があります。

# フィールド

  * `rho::Float64`: 警戒パラメータ: rho ∈ [0, 1].  デフォルト: 0.6
  * `alpha::Float64`: 選択パラメータ: alpha > 0.  デフォルト: 1.0e-7
  * `epsilon::Float64`: マッチトラッキングパラメータ: epsilon ∈ (0, 1).  デフォルト: 0.001
  * `beta::Float64`: 学習パラメータ: beta ∈ (0, 1].  デフォルト: 1.0
  * `max_epochs::Int64`: トレーニング中の最大エポック数: max_epochs ∈ [1, Inf)  デフォルト: 1
  * `uncommitted::Bool`: 未コミットノードフラグ。  デフォルト: true
  * `display::Bool`: 進捗バーの表示フラグ。  デフォルト: false
  * `sort::Bool`: マッチフェーズの前にF2ノードを活性化によってソートするフラグ

    trueの場合、F2ノードはマッチの前に活性化によってソートされます。falseの場合、最適なマッチングユニットを見つけるために反復argmaxおよび抑制手順が使用されます。  デフォルト: false
