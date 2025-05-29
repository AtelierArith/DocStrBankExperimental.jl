```julia
distribute!(pm::ProcessManager, ..., jobs::AbstractJob ...; not::Process = Async) -> ::Vector{Int64}
```

`distribute!` 関数は、すべてのワーカーまたは提供されたワーカーの間でジョブを分配します。

```julia
# 利用可能なすべてのワーカーに分配
distribute!(pm::ProcessManager, jobs::AbstractJob ...)
# 特定のワーカーのみに分配:
distribute!(pm::ProcessManager, worker_pids::Vector{Int64}, jobs::AbstractJob ...)
# ワーカーの割合を分配:
distribute!(pm::ProcessManager, percentage::Float64, jobs::AbstractJob ...)
```

  * 参照: `processes`, `assign!`, `new_job`, `waitfor`, `put!`, `distribute_open!`

---

```example
procs = processes(5)

jb1 = new_job(println, "hello world!")
jb2 = new_job() do
    sleep(5)
    println("job 2")
jb3 = new_job() do 
    sleep(5)
    println("job 3")
end

distribute!(pm, jb1, jb2, jb3)

# `1` と `2` のみに分配
distribute!(pm, [1, 2], jb2, jb3, jb3, jb2, jb1)
```
