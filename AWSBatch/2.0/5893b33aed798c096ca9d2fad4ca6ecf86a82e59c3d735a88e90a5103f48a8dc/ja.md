```
log_events(job::BatchJob) -> Union{Vector{LogEvent}, Nothing}
```

ログストリーム名を取得し、CloudWatchログを取得して、ログイベントのベクターを返します。ログストリームが現在存在しない場合は、`nothing`が返されます。

注意事項：

  * `logStreamName`はジョブがRUNNINGになるまで利用できないため、この関数を呼び出す前に`wait(job)`または`wait(job, [AWSBatch.SUCCEEDED])`を使用することをお勧めします。
