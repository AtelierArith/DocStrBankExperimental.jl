```
schedule_updates(variables...; pipeline_stage = ScheduleOnPipelineStage(PendingScheduler()))
```

Schedules posterior marginal updates for given variables using `stage`. By default creates `ScheduleOnPipelineStage` with `PendingScheduler()` from `Rocket.jl` library. Returns a scheduler with `release!` method available to release all scheduled updates.
