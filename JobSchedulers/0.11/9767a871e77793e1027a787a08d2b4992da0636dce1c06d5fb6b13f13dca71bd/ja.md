```
wait_queue(;show_progress::Bool = false, exit_num_jobs::Int = 0)
```

`queue()`内のすべてのジョブが完了するのを待ちます。

  * `show_progress = true`の場合、ジョブの進行状況が表示されます。
  * `exit_num_jobs::Int`: `queue()`にジョブが`Int`未満の数しかない場合に終了します。常に実行中または再発するジョブを無視するのに便利です。

関連情報: [`queue_progress`](@ref).
