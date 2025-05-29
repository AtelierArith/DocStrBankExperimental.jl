HPCResource - HPCリソース構造体、リソースの占有状況とジョブを追跡するためのもの

  * `nodes::Int64`: ノードの数
  * `node_used_by_job::Vector{Int64}`: そのノードを使用しているジョブIDの配列
  * `node_released_at::Vector{Int64}`: ノードが解放される時間、すでに利用可能な場合は-1
  * `node_released_at_sorted::Vector{Int64}`: node*released*atと同じだがソート済み
  * `queue::Vector{HPCMod.BatchJob}`: キュー内のジョブ
  * `executing::Dict{Int64, HPCMod.BatchJob}`: 現在実行中のジョブ
  * `history::Vector{HPCMod.BatchJob}`: 完了したジョブ
  * `max_nodes_per_job::Int64`
  * `max_time_per_job::Int64`
  * `scheduler_fifo::Bool`
  * `scheduler_backfill::Bool`
  * `stats::HPCMod.HPCResourceStats`
