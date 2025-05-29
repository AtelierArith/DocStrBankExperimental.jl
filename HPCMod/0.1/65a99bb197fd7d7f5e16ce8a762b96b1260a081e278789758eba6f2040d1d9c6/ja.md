全体の単一計算ジョブを実行するために

  * `id::Int64`: CompTask id
  * `user_id::Int64`: このタスクに属するユーザー
  * `nodetime_total::Int64`: このタスクを完了するための合計ノード時間、-1の場合は制限なし
  * `nodetime_left::Int64`: このタスクを完了するための残りノード時間
  * `nodetime_left_unplanned::Int64`: 提出されたジョブを含むこのタスクを完了するための残りノード時間
  * `nodetime_done::Int64`: これまでに完了したノード時間
  * `submit_time::Int64`: タスク提出時間、ユーザーはその時間以降に作業を開始できる
  * `start_time::Int64`: タスク開始時間
  * `end_time::Int64`: 最後のジョブ終了時間
  * `task_split_schema::HPCMod.TaskSplitSchema`: タスク分割の戦略
  * `max_concurrent_jobs::Int64`: 最大同時ジョブ数
  * `nodes_prefered::Int64`: 希望するノード数
  * `walltime_prefered::Int64`: 希望するウォールタイム
  * `current_jobs::Vector{Int64}`: 現在のジョブ、ない場合は0
  * `jobs::Vector{Int64}`: このタスクで作業したジョブのリスト
  * `next_check_time::Int64`: ユーザーによる次のチェック時間、例えば次のバッチジョブを送信するための時間
