```
ACTRScheduler <: AbstractScheduler
```

An ACT-R event scheduler object. 

# Fields

  * `events`: a priority queue of events
  * `time`: current time of the system
  * `running`: simulation can run if true
  * `model_trace`: will print out model events if true
  * `task_trace`: will print out task events if true
  * `store`: will store a vector of completed events if true
  * `complete_events`: an optional vector of completed events
