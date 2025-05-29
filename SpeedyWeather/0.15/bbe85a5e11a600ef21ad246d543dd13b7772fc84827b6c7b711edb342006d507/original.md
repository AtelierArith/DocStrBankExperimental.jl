A schedule for callbacks, to execute them periodically after a given period has passed (first timestep excluded) or on/after specific times (initial time excluded). For two consecutive time steps i, i+1, an event is scheduled at i+1 when it occurs in (i,i+1]. Similarly, a periodic schedule of period p will be executed at start+p, but p is rounded to match the multiple of the model timestep. Periodic schedules and event schedules can be combined, executing at both. A Schedule is supposed to be added into callbacks as fields

```
Base.@kwdef struct MyCallback
    schedule::Schedule = Schedule(every=Day(1))
    other_fields
end
```

see also initialize!(::Schedule,::Clock) and isscheduled(::Schedule,::Clock). Fields

  * `every::Dates.Second`: [OPTION] Execute every time period, first timestep excluded. Default=never.
  * `times::Vector{Dates.DateTime}`: [OPTION] Events scheduled at times
  * `schedule::BitVector`: Actual schedule, true=execute this timestep, false=don't
  * `steps::Int64`: Number of scheduled executions
  * `counter::Int64`: Count up the number of executions
