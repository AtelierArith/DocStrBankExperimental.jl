```
ClusterSequence(algorithm::JetAlgorithm.Algorithm, p::Real, R::Float64, strategy::RecoStrategy.Strategy, jets::T, history, Qtot) where T <: FourMomentum
```

`ClusterSequence`オブジェクトを構築します。

# 引数

  * `algorithm::JetAlgorithm.Algorithm`: クラスタリングに使用されるアルゴリズム。
  * `p::Real`: クラスタリングアルゴリズムに使用されるパワー値。
  * `R::Float64`: クラスタリングアルゴリズムに使用されるRパラメータ。
  * `strategy::RecoStrategy.Strategy`: クラスタリングに使用される戦略。
  * `jets::Vector{T}`: クラスタシーケンス内のジェットで、T <: FourMomentumです。
  * `history::Vector{HistoryElement}`: クラスタシーケンスの分岐履歴。
  * `Qtot::Any`: イベントの総エネルギー。
