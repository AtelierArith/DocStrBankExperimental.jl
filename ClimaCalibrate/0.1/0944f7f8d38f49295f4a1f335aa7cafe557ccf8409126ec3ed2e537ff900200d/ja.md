```
PBSManager(ntasks)
```

PBS/Torque クラスター用の ClusterManager で、`qsub` でリクエストするタスクの数を受け取ります。

`qsub` コマンドを実行するには、`addprocs(PBSManager(ntasks))` を実行します。 [`SlurmManager`](@ref) とは異なり、これはスケジュールされたジョブをネストせず、新しいリソースを取得します。

キーワード引数は `qsub` に渡すことができます: `addprocs(PBSManager(ntasks), nodes=2)`

デフォルトでは、ワーカーは実行中の Julia 環境を継承します。

キャリブレーションを実行するには、`calibrate(WorkerBackend, ...)` を呼び出します。

ワーカーで関数を実行するには、`remotecall(func, worker_id, args...)` を呼び出します。
