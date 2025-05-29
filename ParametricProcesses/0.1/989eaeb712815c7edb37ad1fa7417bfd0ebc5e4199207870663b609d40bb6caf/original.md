```julia
distribute_open!(pm::ProcessManager, job::AbstractJob ...; not::Process = Async) -> ::Vector{Int64}
```

  * See also: `processes`, `assign!`, `new_job`, `waitfor`, `put!`, `distribute!`, `Worker`, `ProcessManager`

---

```example
procs = processes(5)


```
