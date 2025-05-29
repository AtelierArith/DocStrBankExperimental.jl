```julia
mutable struct opts_FuzzyART <: AdaptiveResonance.ARTOpts
```

# 概要

ガンマ正規化ファジーARTオプション構造体。

これらのオプションは、カスタムオプションキーワード引数を取る [`Parameters.jl`](https://github.com/mauro3/Parameters.jl) 構造体です。各フィールドには、以下に示すデフォルト値があります。

# フィールド

  * `rho::Float64`: 警戒パラメータ: rho ∈ [0, 1].  デフォルト: 0.6
  * `alpha::Float64`: 選択パラメータ: alpha > 0.  デフォルト: 0.001
  * `beta::Float64`: 学習パラメータ: beta ∈ (0, 1].  デフォルト: 1.0
  * `gamma::Float64`: 擬似カーネル幅: gamma >= 1.  デフォルト: 3.0
  * `gamma_ref::Float64`: 正規化のための参照ガンマ: 0 <= gamma_ref < gamma.  デフォルト: 1.0
  * `max_epoch::Int64`: トレーニング中の最大エポック数: max_epochs ∈ (1, Inf).  デフォルト: 1
  * `display::Bool`: 進捗バーの表示フラグ。  デフォルト: false
  * `gamma_normalization::Bool`: 特徴次元によってしきい値を正規化するフラグ。

    **注意**: このフラグは、ここでの `activation` と `match` 設定をそのガンマ正規化された同等物に上書きし、しきい値を調整します。  デフォルト: false
  * `uncommitted::Bool`: 学習時に未コミットノードを使用するフラグ。

    trueの場合、新しい重みは ones(dim) で作成され、補完符号化されたサンプルで学習します。 falseの場合、単に補完符号化されたサンプルが新しい重みとして使用される高速コミットが使用されます。  デフォルト: false
  * `activation::Symbol`: 選択された活性化関数。  デフォルト: :basic_activation
  * `match::Symbol`: 選択されたマッチ関数。  デフォルト: :basic_match
  * `update::Symbol`: 選択された重み更新関数。  デフォルト: :basic_update
  * `sort::Bool`: マッチフェーズの前にF2ノードを活性化によってソートするフラグ

    trueの場合、F2ノードはマッチの前に活性化によってソートされます。 falseの場合、最適なマッチングユニットを見つけるために反復argmaxと抑制手順が使用されます。  デフォルト: false
