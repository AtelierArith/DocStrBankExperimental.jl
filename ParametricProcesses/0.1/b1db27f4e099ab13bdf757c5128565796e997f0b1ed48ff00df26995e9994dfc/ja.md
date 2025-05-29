```julia
assign_open!(pm::ProcessManager, job::AbstractJob ...; ; not::Process = Async) -> ::Int64
```

単一の `AbstractJob` をオープンなワーカーに割り当てます。オープンなワーカーが利用できない場合、`distribute!` が呼び出されます。

  * 参照: `processes`, `assign!`, `new_job`, `waitfor`, `put!`, `distribute!`

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
```
