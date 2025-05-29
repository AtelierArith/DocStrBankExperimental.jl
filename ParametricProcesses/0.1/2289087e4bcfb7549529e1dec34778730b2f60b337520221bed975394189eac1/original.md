```julia
ProcessJob <: AbstractJob
```

  * f**::Function**
  * args
  * kwargs

The `ProcessJob` is the default `ParametericProcess` job type. This constructor is also defined as `new_job`. Provide a `Function` and  the arguments for the `Function` to `new_job` (or this constructor), and then provide jobs to a process manager with `assign!` or `distribute!`.

  * See also: `Worker`, `processes`, `ProcessManager`, `assign!`

```julia
- ProcessJob(f::Function, args ...; keyargs ...)
```

---

```example
# note this is `julia --threads >2`
newprocs = processes(3)
io = IOBuffer()
new_job = (io) do o
    write(o, "hello world!)
end

assign!(newprocs, 2, [new_job for e in 1:50] ...)
```
