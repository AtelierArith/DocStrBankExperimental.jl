```julia
mutable struct opts_SFAM <: AdaptiveResonance.ARTOpts
```

# 概要

シンプルファジーARTMAP学習者のオプションを実装します。

これらのオプションは、カスタムオプションのキーワード引数を受け取る[`Parameters.jl`](https://github.com/mauro3/Parameters.jl)構造体です。各フィールドには、以下に示すデフォルト値があります。

# フィールド

  * `rho::Float64`: 警戒パラメータ: rho ∈ [0, 1].  デフォルト: 0.75
  * `alpha::Float64`: 選択パラメータ: alpha > 0.  デフォルト: 1.0e-7
  * `epsilon::Float64`: マッチトラッキングパラメータ: epsilon ∈ (0, 1).  デフォルト: 0.001
  * `beta::Float64`: 学習パラメータ: beta ∈ (0, 1].  デフォルト: 1.0
  * `max_epoch::Int64`: トレーニング中の最大エポック数: max_epoch ∈ [1, Inf).  デフォルト: 1
  * `display::Bool`: 進捗バーの表示フラグ。  デフォルト: false
  * `uncommitted::Bool`: 学習時に未コミットノードを使用するためのフラグ。

    trueの場合、新しい重みはones(dim)で作成され、補完符号化されたサンプルで学習します。falseの場合、新しい重みは単に補完符号化されたサンプルになります。  デフォルト: false
  * `match::Symbol`: 選択されたマッチ関数。  デフォルト: :basic_match
  * `activation::Symbol`: 選択された活性化関数。  デフォルト: :basic_activation
  * `update::Symbol`: 選択された重み更新関数。  デフォルト: :basic_update
  * `sort::Bool`: マッチフェーズの前にF2ノードを活性化によってソートするためのフラグ

    trueの場合、F2ノードはマッチの前に活性化によってソートされます。falseの場合、最適なマッチングユニットを見つけるために反復argmaxおよび抑制手順が使用されます。  デフォルト: false
