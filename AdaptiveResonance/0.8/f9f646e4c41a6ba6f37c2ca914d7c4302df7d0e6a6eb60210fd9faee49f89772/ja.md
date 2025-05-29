```julia
mutable struct DDVFA <: AdaptiveResonance.ART
```

# 概要

分散型デュアルビジランスファジーARTMAPモジュール構造体。

モジュールオプションについては、[`AdaptiveResonance.opts_DDVFA`](@ref)を参照してください。

# 参考文献

1. L. E. Brito da Silva, I. Elnabarawy, and D. C. Wunsch, '分散型デュアルビジランスファジー適応共鳴理論はオンラインで学習し、任意の形状のクラスターを取得し、順序依存性を軽減する,' Neural Networks, vol. 121, pp. 208-228, 2020, doi: 10.1016/j.neunet.2019.08.033.
2. G. Carpenter, S. Grossberg, and D. Rosen, 'ファジーART: 適応共鳴システムによるアナログパターンの高速安定学習と分類,' Neural Networks, vol. 4, no. 6, pp. 759-771, 1991.

# フィールド

  * `opts::AdaptiveResonance.opts_DDVFA`: DDVFAオプション構造体。
  * `subopts::AdaptiveResonance.opts_FuzzyART`: すべてのF2ノードに使用されるFuzzyARTオプション構造体。
  * `config::AdaptiveResonance.DataConfig`: データ構成構造体。
  * `threshold::Float64`: ビジランスパラメータの関数である動作モジュールの閾値値。
  * `F2::Vector{AdaptiveResonance.FuzzyART}`: F2ノードのリスト（それ自体がFuzzyARTモジュール）。
  * `labels::Vector{Int64}`: 各F2ノードに対応するラベルの増分リスト、自己指定または監視されたもの。
  * `n_categories::Int64`: 総カテゴリ数。
  * `epoch::Int64`: 現在のトレーニングエポック。
  * `T::Vector{Float64}`: DDVFAの活性化値。
  * `M::Vector{Float64}`: DDVFAのマッチ値。
  * `stats::Dict{String, Any}`: モジュールのランタイム統計、各トレーニング反復の終わりにエントリを含む辞書として実装されています。これらのエントリには、最もマッチしたユニットのインデックスと、勝利ノードの活性化およびマッチ値が含まれます。
