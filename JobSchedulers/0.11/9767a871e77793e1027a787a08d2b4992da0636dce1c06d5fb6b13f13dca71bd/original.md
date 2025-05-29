```
wait_queue(;show_progress::Bool = false, exit_num_jobs::Int = 0)
```

Wait for all jobs in `queue()` become finished.

  * `show_progress = true`, job progress will show.
  * `exit_num_jobs::Int`: exit when `queue()` has less than `Int` number of jobs. It is useful to ignore some jobs that are always running or recurring.

See also: [`queue_progress`](@ref).
