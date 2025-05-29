```
RuntimeLogRecordMetadata(datetime::DateTime, thread_id::Int, worker_id::Int)

RuntimeLogRecordMetadata(; datetime=Dates.now(), thread_id::Int=Threads.threadid(), worker_id::Int=_worker_id())
```

ランタイムで知られている一般的なログレコードのコンポーネント
