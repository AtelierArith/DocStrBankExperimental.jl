```
yearlength = daysinyear(::Type{DT},y)
```

指定された型 `DT` によるカレンダーに従って、年 `y` の日数を返します。

例

```julia-repl
julia> daysinyear(DateTimeAllLeap,2001,2)
366
```
