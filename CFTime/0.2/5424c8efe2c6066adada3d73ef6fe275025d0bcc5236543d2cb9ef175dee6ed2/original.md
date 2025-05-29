```
yearlength = daysinyear(::Type{DT},y)
```

Returns the number of days in a year for the year `y` according to the calendar given by the type `DT`.

Example

```julia-repl
julia> daysinyear(DateTimeAllLeap,2001,2)
366
```
