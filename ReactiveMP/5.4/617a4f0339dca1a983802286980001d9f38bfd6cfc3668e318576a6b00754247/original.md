```
ScheduleOnPipelineStage{S} <: AbstractPipelineStage
```

Applies the `schedule_on()` operator from `Rocket.jl` library to the given pipeline with a provided `scheduler`

# Arguments

  * `scheduler`: scheduler to schedule updates on. Must be compatible with `Rocket.jl` library and `schedule_on()` operator.
