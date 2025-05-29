```
SlurmRun(;
    slurm_flags::Cmd = {defaults}
    julia_flags::Cmd = {defaults}
    dir = pwd()
    env::Dict{String,String} = Dict{String,String}()
    redirect_output::Bool = true
)
```

Mode to add worker processes via SLURM `srun`.

`srun` and Julia worker `julia` command line flags are inferred from SLURM environment variables (e.g. when inside of an `salloc` or batch job), as well as `slurm_flags` and `julia_flags`.

Workers are started with current directory set to `dir`.

Example:

```julia
runmode = SlurmRun(slurm_flags = `--ntasks=4 --cpus-per-task=8 --mem-per-cpu=8G`)
task = runworkers(runmode)

Threads.@async begin
    wait(task)
    @info "SLURM workers have terminated."
end

@wait_while nprocs()-1 < n
```

Workers can also be started manually, use [`worker_start_command(runmode)`](@ref) to get the `srun` start command and run it from a separate process or so.
