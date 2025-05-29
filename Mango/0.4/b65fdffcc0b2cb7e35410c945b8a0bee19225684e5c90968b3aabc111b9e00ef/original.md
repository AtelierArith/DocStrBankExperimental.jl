```
stop_task(scheduler::AbstractScheduler, t::Task)
```

Stop the task `t` managed by `scheduler`. This only works if the task has been scheduled with the scheduler using a stoppable TaskData.
