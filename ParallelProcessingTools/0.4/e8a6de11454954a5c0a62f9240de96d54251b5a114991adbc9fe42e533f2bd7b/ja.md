```
wait_for_any(
    objs...;
    maxtime::Union{Real,Nothing} = nothing, timeout_error::Bool = false
)

wait_for_all(objs::Union{Tuple,AbstractVector,Base.Generator,Base.ValueIterator}; kwargs...)
```

オブジェクト `objs` のいずれかが準備完了になるのを待ちます。

オブジェクトの準備完了は [`wouldwait`](@ref) によって定義されます。`Nothing` のオブジェクトは無視され、つまり待機されません。

`maxtime` と `timeout_error` の効果については [`@wait_while`](@ref) を参照してください。

例として、タイムアウト付きでタスクを待機します：

```julia
task1 = Threads.@spawn sleep(1.0)
task2 = Threads.@spawn sleep(5.0)
wait_for_any(task1, task2, maxtime = 3.0)
istaskdone(task1) == true
istaskdone(task2) == false
```

`waitany`（Julia v1.12で新しく追加）に似ていますが、より広範なオブジェクトタイプに適用されます。
