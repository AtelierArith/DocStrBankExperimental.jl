```
monthlength = daysinmonth(::Type{DT},y,m)
```

指定された型 `DT` によるカレンダーに従って、年 `y` と月 `m` の月の日数を返します。

例

```julia-repl
julia> daysinmonth(DateTimeAllLeap,2001,2)
29
```
