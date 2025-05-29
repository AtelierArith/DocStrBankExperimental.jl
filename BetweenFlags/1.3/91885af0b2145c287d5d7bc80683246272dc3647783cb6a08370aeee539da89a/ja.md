```
FlagPair(start::Flag, stop::Flag)
```

興味のある部分文字列の開始と終了を定義するフラグペアです。

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
