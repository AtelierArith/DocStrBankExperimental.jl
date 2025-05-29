```
wait_for_all(
    objs...;
    maxtime::Union{Real,Nothing} = nothing, timeout_error::Bool = false
)

wait_for_all(objs::Union{Tuple,AbstractVector,Base.Generator,Base.ValueIterator}; kwargs...)
```

すべての `objs` が準備完了になるのを待ちます。

オブジェクトの準備完了は [`wouldwait`](@ref) によって定義されます。 `Nothing` のオブジェクトは無視され、すなわち待機されません。

`maxtime` と `timeout_error` の効果については [`@wait_while`](@ref) を参照してください。

例として、2つのタスクが終了するのを待ちます：

```julia
task1 = Threads.@spawn sleep(10)
task2 = Threads.@spawn sleep(2)
wait_for_all(task1, task2)
```
