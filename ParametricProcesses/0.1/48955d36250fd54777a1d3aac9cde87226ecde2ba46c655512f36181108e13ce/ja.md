```julia
assign!
```

`assign!` は、タスクをワーカーに直接配布するために使用されます。これは2つの形態に集約されます。`assign!` は、ワーカーをそのプロセスタイプを使用して直接その仕事に割り当てるために使用され、またプロセスマネージャのワーカーを仕事に `assign!` するためにも使用されます。

```julia
# ワーカーを直接割り当てるために使用:
assign!(assigned_worker::Worker{Threaded}, job::AbstractJob)
assign!(f::Function, assigned_worker::Worker{:Threaded}, job::AbstractJob)
# `ProcessManager` を介して割り当てるために使用:
   #   vvv `jobs` の完了時に `f` を実行します。
assign!(f::Function, pm::ProcessManager, pid::Any, jobs::AbstractJob ...)

assign!(pm::ProcessManager, pid::Any, jobs::AbstractJob ...)
```

  * 参照: `processes`, `distribute!`, `waitfor`, `put!`, `new_job`, `assign_open!`

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

assign!(procs, 2, jb2)
```
