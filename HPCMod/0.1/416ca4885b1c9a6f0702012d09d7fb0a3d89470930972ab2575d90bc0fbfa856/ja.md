ユーザー

  * `id::Int64`
  * `pos::Tuple{Int64}`
  * `max_concurrent_tasks::Int64`: 最大同時タスク数
  * `max_nodes_per_job::Int64`: ジョブごとの最大ノード数, -1 - 制約なし
  * `max_time_per_job::Int64`: ジョブごとの最大壁時間, -1 - 制約なし
  * `tasks_to_do::DataStructures.SortedSet{HPCMod.CompTask}`
  * `tasks_active::Vector{HPCMod.CompTask}`
  * `tasks_done::Vector{HPCMod.CompTask}`
  * `jobs_to_process::Vector{HPCMod.BatchJob}`: ユーザーが処理するための完了したジョブ
  * `inividual_jobs_task::HPCMod.CompTask`: 個別ジョブのためのCompTask
  * `inividual_jobs::DataStructures.SortedSet{HPCMod.BatchJob}`: タスクにバインドされていないジョブ
  * `thinktime_generator::Function`
