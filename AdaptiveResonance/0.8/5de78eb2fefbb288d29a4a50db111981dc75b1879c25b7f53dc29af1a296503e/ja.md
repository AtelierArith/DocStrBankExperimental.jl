```julia
mutable struct opts_DDVFA <: AdaptiveResonance.ARTOpts
```

# 概要

分散デュアル警戒ファジーARTオプション構造体。

これらのオプションは、カスタムオプションキーワード引数を取る[`Parameters.jl`](https://github.com/mauro3/Parameters.jl)構造体です。各フィールドには、以下に示すデフォルト値があります。

# フィールド

  * `rho_lb::Float64`: 下限警戒パラメータ: rho_lb ∈ [0, 1].  デフォルト: 0.7
  * `rho_ub::Float64`: 上限警戒パラメータ: rho_ub ∈ [0, 1].  デフォルト: 0.85
  * `alpha::Float64`: 選択パラメータ: alpha > 0.  デフォルト: 0.001
  * `beta::Float64`: 学習パラメータ: beta ∈ (0, 1].  デフォルト: 1.0
  * `gamma::Float64`: 擬似カーネル幅: gamma >= 1.  デフォルト: 3.0
  * `gamma_ref::Float64`: 正規化のための参照ガンマ: 0 <= gamma_ref < gamma.  デフォルト: 1.0
  * `similarity::Symbol`: 類似性メソッド（活性化とマッチ）: similarity ∈ [:single, :average, :complete, :median, :weighted, :centroid].  デフォルト: :single
  * `max_epoch::Int64`: 学習中の最大エポック数: max_epochs ∈ (1, Inf).  デフォルト: 1
  * `display::Bool`: 進捗バーの表示フラグ。  デフォルト: false
  * `gamma_normalization::Bool`: 特徴次元によって閾値を正規化するフラグ。  デフォルト: true
  * `uncommitted::Bool`: 学習時に未コミットノードを使用するフラグ。

    trueの場合、新しい重みはones(dim)で作成され、補完符号化されたサンプルで学習します。falseの場合、新しい重みは単に補完符号化されたサンプルになります。  デフォルト: false
  * `activation::Symbol`: 選択された活性化関数。  デフォルト: :gamma_activation
  * `match::Symbol`: 選択されたマッチ関数。  デフォルト: :gamma_match
  * `update::Symbol`: 選択された重み更新関数。  デフォルト: :basic_update
  * `sort::Bool`: マッチフェーズの前にF2ノードを活性化によってソートするフラグ

    trueの場合、F2ノードはマッチの前に活性化によってソートされます。falseの場合、最適なマッチングユニットを見つけるために反復argmaxと抑制手順が使用されます。  デフォルト: false
