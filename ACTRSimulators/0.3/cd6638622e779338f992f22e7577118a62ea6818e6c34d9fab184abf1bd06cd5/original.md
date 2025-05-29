```
ACTRScheduler(;event=Event, time=0.0, running=true, model_trace=false, task_trace=false, store=false)
```

Constructor for Scheduler with default keyword values:

# Keywords

  * `event`: a function that is executed at the specified time
  * `time`: the time at which the event will be execute
  * `running`: whether the model is running
  * `model_trace`: prints model trace if true
  * `task_trace`: prints task trace if true
  * `store`: stores the executed events for replay if set to true
