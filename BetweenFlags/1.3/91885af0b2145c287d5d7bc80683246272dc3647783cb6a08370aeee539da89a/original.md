```
FlagPair(start::Flag, stop::Flag)
```

A flag pair that defines the start and stop of the substring of interest.

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
flag_pair = FlagPair(start_flag, stop_flag)
```
