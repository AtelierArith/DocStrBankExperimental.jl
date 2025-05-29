```
Flag(flag::String,
     flag_boundaries_left::Vector{String},
     flag_boundaries_right::Vector{String})
```

A flag that BetweenFlags looks for to denote the start/stop position of a given scope. The flag boundaries need only be unique since every permutation of left and right flag boundaries are taken to determine scopes.

```julia
julia>
using BetweenFlags
# find: ["\nfunction", " function", ";function"]
start_flag = Flag("function",
                  ["\n", "\s", ";"],
                  ["\n", "\s"],
                  StartType())
# find: ["\nend", " end", ";end"]
stop_flag = Flag("end",
                 ["\n", "\s", ";"],
                 ["\n", "\s", ";"],
                 StopType())
```
