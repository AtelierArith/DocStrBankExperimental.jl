```julia
struct ComputationSettings{T<:Integer}
```

# Description

Computational settings

# Fields

  * `location`: where computation is performed. 'local' and 'slurm' are supported presently Default: local
  * `num_procs`: Number of processes. Giving 1 avoids multiprocessing (since adding only one worker would have negative effect on performance, as master is not used in the loop). On a cluster give number of nodes (Should double check this). Default: 1
  * `num_tasks`: Number of tasks per process. Giving somewhat more than the number of actual ( virtual or physical ?? ) threads is probably a good idea.   Default: Threads.nthreads() * 2
  * `num_threads`: Number of threads that each processes are started with. Default: num_tasks
  * `maxmem`: Trigger intensive garbage collection at this memory usage Default: -1
  * `clustermanager_settings`: Other settings Default: Dict(:x => "")
