```
set_scheduler(;
    max_cpu::Real = JobSchedulers.SCHEDULER_MAX_CPU,
    max_mem::Real = JobSchedulers.SCHEDULER_MAX_MEM,
    max_job::Int = JobSchedulers.JOB_QUEUE.max_done,
    max_cancelled_job::Int = JobSchedulers.JOB_QUEUE.max_cancelled_job
)
```

  * `max_job`: the number of jobs done. If number of jobs exceed 1.5*NUMBER, old jobs will be delete.
  * `max_cancelled_job`: the number of cancelled jobs. If number of jobs exceed 1.5*NUMBER, old jobs will be delete.

See details: [`set_scheduler_max_cpu`](@ref),  [`set_scheduler_max_mem`](@ref),  [`set_scheduler_max_job`](@ref)
