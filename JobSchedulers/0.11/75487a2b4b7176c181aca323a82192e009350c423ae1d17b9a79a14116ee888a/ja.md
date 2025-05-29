```
queue_progress(;remove_tmp_files::Bool = true, kwargs...)
queue_progress(stdout_tmp::IO, stderr_tmp::IO;
group_seperator = GROUP_SEPERATOR, wait_second_for_new_jobs::Int = 1, loop::Bool = true, exit_num_jobs::Int = 0)
```

  * `group_seperator`: `(job::Job).name` をグループ名と特定のジョブ名に分割するための区切り文字。
  * `wait_second_for_new_jobs::Int`: `auto_exit` の場合、すべてのジョブが過去にあるとき、`queue_progress` をすぐに終了せず、一定の期間待機します。新しいジョブが提出された場合、`queue_progress` を終了しません。
  * `loop::Bool`: false の場合、現在の進捗のみを表示して終了します。
  * `exit_num_jobs::Int`: `queue()` にジョブが `Int` 数未満のときに終了します。常に実行中または再発するジョブを無視するのに便利です。
