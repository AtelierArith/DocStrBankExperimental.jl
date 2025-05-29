```
monthlength = daysinmonth(::Type{DT},y,m)
```

Returns the number of days in a month for the year `y` and the month `m` according to the calendar given by the type `DT`.

Example

```julia-repl
julia> daysinmonth(DateTimeAllLeap,2001,2)
29
```
