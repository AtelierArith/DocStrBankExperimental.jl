```
Loop{T, S<:Integer}
Loop(f, period)
```

Create a schedule that loops `f` every `period` iterations. `f` must be callabe (a function or schedule).

# Arguments

  * `f`: the schedule to loop
  * `period::Integer`: how often to loop
