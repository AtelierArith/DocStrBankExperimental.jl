```
ensure_procinit(pid::Int)
ensure_procinit(pids::AbstractVector{Int} = workers())
```

必要に応じて、指定されたプロセスでプロセス初期化コードを実行し、初期化が完了した後に戻ります。

[`FlexWorkerPool`](@ref)を使用する場合、プールが完全に初期化されるまで、ワーカーの初期化は安全にバックグラウンドで実行できます（プールは`take!(pool)`を介してワーカーを提供します）。

[`ParallelProcessingTools.get_procinit_code`](@ref)および[`ParallelProcessingTools.add_procinit_code`](@ref)も参照してください。

[`ParallelProcessingTools.get_procinit_code`](@ref)、[`ParallelProcessingTools.ensure_procinit`](@ref)、[`ParallelProcessingTools.global_procinit_level`](@ref)、および[`ParallelProcessingTools.current_procinit_level`](@ref)も参照してください。
