```
BendersAlgorithm(graph, root_object; kwargs...)
```

`graph`からBendersAlgorithmオブジェクトを作成するための関数。`root_object`はOptiNodeまたは`graph`上のサブグラフでなければなりません。キーワード引数には以下が含まれます。

  * `max_iters = 100` - 最大反復回数
  * `tol = 1e-7` - 上限と下限の間の終了許容誤差
  * `M = 0` - 各ノードのコスト推定値の下限
  * `is_MIP = nothing` - 問題がMIPであるかどうかを示します。`nothing`として渡された場合、PlasmoBendersはそれがMIPであるかどうかを確認し、`is_MIP`を適切に設定します
  * `solver = nothing` - 定義されている場合、このソルバーはすべてのサブ問題に設定されます
  * `strengthened = false` - 強化されたBendersカットを使用するかどうか（https://doi.org/10.1007/s10107-018-1249-5を参照）
  * `multicut = true` - 適用可能な場合、マルチカット（集約カットではなく）を使用するかどうか
  * `feasibility_cuts = false` - フィージビリティカットを許可するかどうか
  * `regularize = false` - 次の反復の解を正則化するかどうか
  * `parallelize_benders = false` - 問題にBenders型構造が定義されている場合、サブ問題の解を並列化するかどうか
  * `parallelize_forward = false` - 可能であれば前方パスを並列化するかどうか；まだサポートされていません
  * `parallelize_backward = false` - 後方パスを並列化するかどうか
  * `add_slacks::Bool = false` - 解の間のフィージビリティを確保するためにリンク制約にスラック変数を追加するかどうか；スラック変数は目的関数でペナルティが課されます
  * `fix_slacks = false` - スラック変数をゼロに固定するかどうか；問題が非フィージブルな場合のみ緩和されます
  * `warm_start::Bool = true` - 前の反復の解を次の反復の前方パスの開始値として設定するかどうか
  * `relaxed_init_cuts = false` - 問題を緩和して全体の問題を解くことによって初期カットを生成するかどうか；MILPにのみ適用されます
  * `slack_penalty = 1e6` - 目的関数におけるスラック変数の係数
  * `regularize_param = 0.5` - 正則化パラメータ；0と1の間でなければなりません
