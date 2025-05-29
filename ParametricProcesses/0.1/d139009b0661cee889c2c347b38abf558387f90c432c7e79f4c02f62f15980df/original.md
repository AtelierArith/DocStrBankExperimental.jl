```julia
distribute!(pm::ProcessManager, ..., jobs::AbstractJob ...; not::Process = Async) -> ::Vector{Int64}
```

The `distribute!` Function will distribute jobs amongst all workers or amongst  the provided workers.

```julia
# distribute to all available workers
distribute!(pm::ProcessManager, jobs::AbstractJob ...)
# distribute only to certain workers:
distribute!(pm::ProcessManager, worker_pids::Vector{Int64}, jobs::AbstractJob ...)
# distribute a percentage of workers:
distribute!(pm::ProcessManager, percentage::Float64, jobs::AbstractJob ...)
```

  * See also: `processes`, `assign!`, `new_job`, `waitfor`, `put!`, `distribute_open!`

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

# distribute to only `1` and `2`
distribute!(pm, [1, 2], jb2, jb3, jb3, jb2, jb1)
```
