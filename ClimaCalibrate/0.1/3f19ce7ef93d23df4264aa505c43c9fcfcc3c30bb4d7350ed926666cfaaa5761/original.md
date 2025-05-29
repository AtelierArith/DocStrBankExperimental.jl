```
add_workers(
    nworkers;
    device = :gpu,
    cluster = :auto,
    kwargs...
)
```

Add `nworkers` worker processes to the current Julia session, automatically detecting and configuring for the available computing environment.

# Arguments

  * `nworkers::Int`: The number of worker processes to add.
  * `device::Symbol = :gpu`: The target compute device type, either `:gpu` (1 GPU, 4 CPU cores) or `:cpu` (1 CPU core).
  * `cluster::Symbol = :auto`: The cluster management system to use. Options:

      * `:auto`: Auto-detect available cluster environment (SLURM, PBS, or local)
      * `:slurm`: Force use of SLURM scheduler
      * `:pbs`: Force use of PBS scheduler
      * `:local`: Force use of local processing (standard `addprocs`)
  * `kwargs`: Other kwargs can be passed directly through to `addprocs`.
