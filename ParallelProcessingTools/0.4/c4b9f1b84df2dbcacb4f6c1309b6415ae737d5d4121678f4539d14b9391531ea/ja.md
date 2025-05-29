```
runworkers(
    runmode::ParallelProcessingTools.RunProcsMode
    manager::Distributed.AbstractClusterManager = ppt_cluster_manager()
)
```

Julia ワーカープロセスを実行します。

デフォルトでは、すべてのワーカープロセスが現在のプロセスと同じ Julia プロジェクト環境を使用することを保証します（計算ホスト間でファイルシステムパスが一貫している必要があります）。

新しいワーカーは [`ppt_cluster_manager()`](@ref) を介して管理され、自動的に [`ppt_worker_pool()`](@ref) に追加されます。

タプル `(task, n)` を返します。ここで、`task::Task` はすべてのワーカーが終了したときに完了します。`n` は、開始されるワーカーの数が既知であれば `Integer` であり、ワーカーの数が正確に予測できない場合は `Nothing` です。

例:

```julia
task, n = runworkers(OnLocalhost(n = 4))
```

詳細は [`worker_resources()`](@ref) を参照してください。
