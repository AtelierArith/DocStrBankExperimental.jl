```
queue_progress(;remove_tmp_files::Bool = true, kwargs...)
queue_progress(stdout_tmp::IO, stderr_tmp::IO;
group_seperator = GROUP_SEPERATOR, wait_second_for_new_jobs::Int = 1, loop::Bool = true, exit_num_jobs::Int = 0)
```

  * `group_seperator`: delim to split `(job::Job).name` to group and specific job names.
  * `wait_second_for_new_jobs::Int`: if `auto_exit`, and all jobs are PAST, not quiting `queue_progress` immediately but wait for a period. If new jobs are submitted, not quiting `queue_progress`.
  * `loop::Bool`: if false, only show the current progress and exit.
  * `exit_num_jobs::Int`: exit when `queue()` has less than `Int` number of jobs. It is useful to ignore some jobs that are always running or recurring.
