バッチジョブは、CompTaskの管理可能な部分を表します。

  * `id::Int64`: ジョブID - 小さいIDは必ずしも早い提出を保証するわけではありません
  * `task::HPCMod.CompTask`
  * `nodes::Int64`
  * `walltime::Int64`
  * `submit_time::Int64`
  * `start_time::Int64`
  * `end_time::Int64`
  * `scheduled_by::HPCMod.SchedulerType`
  * `nodes_list::Vector{Int64}`: ノードIDのベクター
