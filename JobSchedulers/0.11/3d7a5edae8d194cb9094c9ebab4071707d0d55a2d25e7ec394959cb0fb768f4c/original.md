```
set_scheduler_max_job(max_done::Int = 10000, max_cancelled::Int = max_done)
```

Set the number of finished jobs. If number of jobs exceed 1.5*NUMBER, old jobs will be delete.
