```
OnLocalhost(;
    n::Integer = 1
    env::Dict{String,String} = Dict{String,String}()
) isa DynamicAddProcsMode
```

Mode that runs `n` worker processes on the current host.

Example:

```julia
runmode = OnLocalhost(n = 4)
task, n = runworkers(runmode)

Threads.@async begin
    wait(task)
    @info "SLURM workers have terminated."
end

@wait_while nprocs()-1 < n)
```

Workers can also be started manually, use [`worker_start_command(runmode)`](@ref) to get the system (shell) command and run it from a separate process or so.
