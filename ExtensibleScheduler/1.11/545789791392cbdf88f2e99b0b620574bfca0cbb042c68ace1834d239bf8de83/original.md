```
iterate(trigger, dt[, n=number_of_times])
```

Iterate from instant `dt` using trigger with a given iteration number `n`  if `n < 0` (`-1` by default), it iterates indefinitely.

# Usage

```
julia> trigger = Trigger(Dates.Time(20, 30))

julia> for dt in iterate(trigger, DateTime(2020, 1, 1), n=3)
         @show dt
       end
dt = 2020-01-01T20:30:00
dt = 2020-01-02T20:30:00
dt = 2020-01-03T20:30:00

julia> collect(iterate(trigger, DateTime(2020, 1, 1), n=3))
3-element Array{Any,1}:
 2020-01-01T20:30:00
 2020-01-02T20:30:00
 2020-01-03T20:30:00
```
