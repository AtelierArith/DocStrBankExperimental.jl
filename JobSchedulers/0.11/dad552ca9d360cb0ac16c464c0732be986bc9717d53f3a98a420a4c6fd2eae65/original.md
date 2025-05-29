```
solve_optimized_ncpu(default::Int; 
    ncpu_range::UnitRange{Int} = 1:total_cpu, 
    njob::Int = 1, 
    total_cpu::Int = JobSchedulers.SCHEDULER_MAX_CPU, 
    side_jobs_cpu::Int = 0)
```

Find the optimized number of CPU for a job.

  * `default`: default ncpu of the job.
  * `ncpu_range`: the possible ncpu range of the job.
  * `njob`: number of the same job.
  * `total_cpu`: the total CPU that can be used by JobSchedulers.
  * `side_jobs_cpu`: some small jobs that might be run when the job is running, so the job won't use up all of the resources and stop small tasks.
