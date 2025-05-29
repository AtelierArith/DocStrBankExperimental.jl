```
set_scheduler(;
    max_cpu::Real = JobSchedulers.SCHEDULER_MAX_CPU,
    max_mem::Real = JobSchedulers.SCHEDULER_MAX_MEM,
    max_job::Int = JobSchedulers.JOB_QUEUE.max_done,
    max_cancelled_job::Int = JobSchedulers.JOB_QUEUE.max_cancelled_job
)
```

  * `max_job`: 完了したジョブの数。ジョブの数が1.5*NUMBERを超えると、古いジョブは削除されます。
  * `max_cancelled_job`: キャンセルされたジョブの数。ジョブの数が1.5*NUMBERを超えると、古いジョブは削除されます。

詳細については: [`set_scheduler_max_cpu`](@ref),  [`set_scheduler_max_mem`](@ref),  [`set_scheduler_max_job`](@ref)
