```
SlurmManager(ntasks=get(ENV, "SLURM_NTASKS", 1))
```

Slurmクラスタ用のClusterManagerで、`srun`でリクエストするタスクの数を受け取ります。

`srun`コマンドを実行するには、`addprocs(SlurmManager(ntasks))`を実行します。

キーワード引数は`srun`に渡すことができます：`addprocs(SlurmManager(ntasks), gpus_per_task=1)`

デフォルトでは、ワーカーは実行中のJulia環境を継承します。

キャリブレーションを実行するには、`calibrate(WorkerBackend, ...)`を呼び出します。

ワーカーで関数を実行するには、`remotecall(func, worker_id, args...)`を呼び出します。
