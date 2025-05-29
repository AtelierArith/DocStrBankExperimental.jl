```julia
mutable struct DVFA <: AdaptiveResonance.AbstractFuzzyART
```

# 概要

デュアルバイジランスファジーARTMAPモジュール構造体。

モジュールオプションについては、[`AdaptiveResonance.opts_DVFA`](@ref)を参照してください。

# 参考文献:

1. L. E. Brito da Silva, I. Elnabarawy and D. C. Wunsch II, 'Dual Vigilance Fuzzy ART,' Neural Networks Letters. 掲載予定。
2. G. Carpenter, S. Grossberg, and D. Rosen, 'Fuzzy ART: Fast stable learning and categorization of analog patterns by an adaptive resonance system,' Neural Networks, vol. 4, no. 6, pp. 759-771, 1991.

# フィールド

  * `opts::AdaptiveResonance.opts_DVFA`: DVFAオプション構造体。
  * `config::AdaptiveResonance.DataConfig`: データ構成構造体。
  * `threshold_ub::Float64`: 動作上限モジュール閾値値、上限バイジランスパラメータの関数。
  * `threshold_lb::Float64`: 動作下限モジュール閾値値、下限バイジランスパラメータの関数。
  * `labels::Vector{Int64}`: 各F2ノードに対応するラベルの増分リスト、自己指定または監視されたもの。
  * `W::ElasticArrays.ElasticMatrix{Float64, V} where V<:DenseVector{Float64}`: カテゴリ重み行列。
  * `T::Vector{Float64}`: 特定のサンプルに対する各重みの活性化値。
  * `M::Vector{Float64}`: 特定のサンプルに対する各重みのマッチ値。
  * `n_categories::Int64`: カテゴリ重みの数（F2ノード）。
  * `n_clusters::Int64`: ラベル付きクラスタの数、`n_categories`より少ない場合がある。
  * `epoch::Int64`: 現在のトレーニングエポック。
  * `stats::Dict{String, Any}`: モジュールのランタイム統計、各トレーニング反復の終わりにエントリを含む辞書として実装されています。これらのエントリには、最も適合したユニットのインデックスと、勝利ノードの活性化およびマッチ値が含まれます。
