```
Flag(flag::String,
     flag_boundaries_left::Vector{String},
     flag_boundaries_right::Vector{String})
```

与えられたスコープの開始/停止位置を示すためにBetweenFlagsが探すフラグ。フラグの境界は一意である必要があるだけで、すべての左および右のフラグ境界の順列がスコープを決定するために考慮されます。

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
