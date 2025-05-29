```
ppt_worker_pool()
```

デフォルトのParallelProcessingToolsワーカープールを返します。

デフォルトのインスタンスがまだ存在しない場合、最初に`Distributed.myid()`を唯一のワーカーとして含む`FlexWorkerPool`が作成されます。
