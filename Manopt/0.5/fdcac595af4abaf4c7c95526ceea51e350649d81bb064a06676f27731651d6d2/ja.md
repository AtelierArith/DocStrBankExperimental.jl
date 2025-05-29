```
MeshAdaptiveDirectSearchState <: AbstractManoptSolverState
```

# フィールド

  * `p::P`: マニフォールド $\mathcal M$ 上の点で、現在の反復を格納します
  * `mesh_size`: 現在の（内部の）メッシュサイズ
  * `scale_mesh`: 内部メッシュサイズの現在のスケーリングで、実際に使用されるメッシュサイズを生成します
  * `max_stepsize`: ポールまたは検索で候補を探す際に取る最長ステップの上限
  * `poll_size`
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ
  * `poll::`[`AbstractMeshPollFunction`]: 実行するポールステップ（ファンクタ）
  * `search::`[`AbstractMeshSearchFunction`}(@ref) 実行する検索ステップ（ファンクタ）
