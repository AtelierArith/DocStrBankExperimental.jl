```
struct ClusterSequence
```

ジェットクラスタリングシーケンスの完全な履歴を保持する構造体で、最終的なジェットを含みます。

# フィールド

  * `algorithm::JetAlgorithm.Algorithm`: クラスタリングに使用されるアルゴリズム。
  * `strategy::RecoStrategy.Strategy`: クラスタリングに使用される戦略。
  * `power::Float64`: クラスタリングアルゴリズムに使用されるパワー値（この値は常にFloat64として保存され、型の安定性が保たれます）。
  * `R::Float64`: クラスタリングアルゴリズムに使用されるRパラメータ。
  * `jets::Vector{T}`: クラスタシーケンス内の実際のジェットで、型は`T <: FourMomentum`です。
  * `n_initial_jets::Int`: 排他的なジェットに使用される初期の粒子数。
  * `history::Vector{HistoryElement}`: クラスタシーケンスの分岐履歴。履歴の各段階は、物理的なPseudoJetを取得するためにジェットベクター内のどこを見ればよいかを示します。
  * `Qtot::Any`: イベントの総エネルギー。
