```
schedule_global(release!, T, m, endtime; kill=false, pass_schedule=false)
```

Simulate a preemptive global schedule of task system `T` on `m` processors to the specified `endtime`.  When releasing a job, the function `release!(job)` is called, allowing arbitrary modifications to be made, enabling a wide variety of global schedulers to be implemented.  Three examples are provided: [`schedule_gfp`](@ref), [`schedule_gedf`](@ref), and [`schedule_gfl`](@ref).

The `job` provided to `release!(job)` defaults to being released as early as possible (i.e. at time 0 or one period after the task's last job), and has the relative deadline and cost specified by the task.  The priority defaults to the task's index in `T`, with lower priority values being treated as higher priority by the scheduler.

If `kill` is `true`, jobs are killed at their deadline if they have not yet completed.

If `pass_schedule` is `true`, the `release!` function is passed a second argument containing the schedule up until the job's release.
