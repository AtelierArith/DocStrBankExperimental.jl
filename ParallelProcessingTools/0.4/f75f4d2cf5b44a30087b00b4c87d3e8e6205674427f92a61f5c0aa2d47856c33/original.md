```
HTCondorRun(;
    n::Int = 1
    condor_flags::Cmd = _default_condor_flags()
    condor_settings::Dict{String,String} = Dict{String,String}()
    julia_flags::Cmd = _default_julia_flags()
    julia_depot::Vector{String} = DEPOT_PATH
    jobfile_dir = homedir()
    env::Dict{String,String} = Dict{String,String}()
    redirect_output::Bool = true
)
```

Mode to add worker processes via HTCondor `condor_submit`.

Condor submit script and steering `.sh` files are stored in `jobfile_dir`.

Example:

```julia-repl
julia> runmode = HTCondorRun(n = 10; condor_settings=Dict("universe" => "vanilla", "+queue" => "short", "request_memory" => "4GB"))
task = runworkers(runmode)

julia> runworkers(runmode)
[ Info: Submitting HTCondor job: `condor_submit /home/jiling/jl_rAHyFadwHa.sub`
Submitting job(s)..........
10 job(s) submitted to cluster 3198291.
[ Info: HTCondor job submitted: `condor_submit /home/jiling/jl_rAHyFadwHa.sub`
(nothing, 10)

julia> sleep(10)

julia> nworkers()
10
```

Workers can also be started manually, use [`worker_start_command(runmode)`](@ref) to get the `condor_submit` start command and run it from a separate process or so.
