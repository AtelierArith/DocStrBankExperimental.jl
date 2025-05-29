```julia
assign!
```

`assign!` is used to distribute tasks to workers directly. This  culminates in two forms; `assign!` is used to assign a worker directly to  its job using its process type and it is also used to `assign!` a process  manager's workers to jobs.

```julia
# used to assign workers directly:
assign!(assigned_worker::Worker{Threaded}, job::AbstractJob)
assign!(f::Function, assigned_worker::Worker{:Threaded}, job::AbstractJob)
# used to assign via a `ProcessManager`:
   #   vvv does `f` on completion of `jobs`.
assign!(f::Function, pm::ProcessManager, pid::Any, jobs::AbstractJob ...)

assign!(pm::ProcessManager, pid::Any, jobs::AbstractJob ...)
```

  * See also: `processes`, `distribute!`, `waitfor`, `put!`, `new_job`, `assign_open!`

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
