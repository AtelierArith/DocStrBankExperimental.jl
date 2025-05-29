```
issinglearc(radec::Vector{RadecMPC{T}}, arc::Day = Day(30)) where {T <: Real}
```

Check whether `radec` is a single observational arc, i.e. no two consecutive observations are more than `arc` days apart. The function assumes `radec` is sorted.
