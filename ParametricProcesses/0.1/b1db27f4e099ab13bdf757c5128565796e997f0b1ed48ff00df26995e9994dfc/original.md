```julia
assign_open!(pm::ProcessManager, job::AbstractJob ...; ; not::Process = Async) -> ::Int64
```

Assigns a single `AbstractJob` to an open worker. If no open workers are available, `distribute!` will be called.

  * See also: `processes`, `assign!`, `new_job`, `waitfor`, `put!`, `distribute!`

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
