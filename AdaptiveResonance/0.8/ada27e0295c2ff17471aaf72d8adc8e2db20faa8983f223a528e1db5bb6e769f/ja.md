```julia
mutable struct FuzzyART <: AdaptiveResonance.AbstractFuzzyART
```

# 概要

ガンマ正規化されたFuzzy ART学習者構造体

モジュールオプションについては、[`AdaptiveResonance.opts_FuzzyART`](@ref)を参照してください。

# 参考文献

1. G. Carpenter, S. Grossberg, and D. Rosen, 'Fuzzy ART: Fast stable learning and categorization of analog patterns by an adaptive resonance system,' Neural Networks, vol. 4, no. 6, pp. 759-771, 1991.

# フィールド

  * `opts::AdaptiveResonance.opts_FuzzyART`: FuzzyARTオプション構造体。
  * `config::AdaptiveResonance.DataConfig`: データ構成構造体。
  * `threshold::Float64`: 操作モジュールの閾値、警戒パラメータの関数。
  * `labels::Vector{Int64}`: 各F2ノードに対応するラベルの増分リスト、自己指定または監視されたもの。
  * `T::Vector{Float64}`: 特定のサンプルに対する各重みの活性化値。
  * `M::Vector{Float64}`: 特定のサンプルに対する各重みのマッチ値。
  * `W::ElasticArrays.ElasticMatrix{Float64, V} where V<:DenseVector{Float64}`: カテゴリ重み行列。
  * `n_instance::Vector{Int64}`: 各カテゴリに関連付けられた重みの数。
  * `n_categories::Int64`: カテゴリ重みの数（F2ノード）。
  * `epoch::Int64`: 現在のトレーニングエポック。
  * `stats::Dict{String, Any}`: モジュールのランタイム統計、各トレーニングイテレーションの終わりにエントリを含む辞書として実装されています。これらのエントリには、最も適合したユニットのインデックスと、勝利ノードの活性化およびマッチ値が含まれます。
