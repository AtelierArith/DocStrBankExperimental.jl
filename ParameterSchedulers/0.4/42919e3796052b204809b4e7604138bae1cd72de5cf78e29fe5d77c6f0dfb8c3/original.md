```
Sequence{T, S}
Sequence(schedules, step_sizes)
Sequence(schedule1 => step1, schedule2 => step2, ...)
```

A sequence of schedules. The output of this schedule is the concatenation of `schedules` where each schedule is evaluated for each step size in `step_sizes`.

Note that `schedules` can also be a vector of numbers (not just schedules).

# Arguments

  * `schedules`: a vector of schedules or numbers
  * `step_sizes`: a vector of iteration lengths for each schedule
