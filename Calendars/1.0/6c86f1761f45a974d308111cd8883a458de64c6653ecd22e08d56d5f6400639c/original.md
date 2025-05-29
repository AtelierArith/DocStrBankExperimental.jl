```julia
Duration(a::CDate, b::CDate, show=false)
```

The duration gives the number of days between the two dates `a` and `b`,  counting the first date but not the second. So it describes a right  half-open time interval. The start and end dates can be given in  different calendars.

If the optional parameter `show` is set to 'true', both dates are  printed. `show` is 'false' by default.

```julia
julia> Duration((CE, 2022, 1, 1), (ID, 2022, 1, 1), true)
```

Perhaps to the surprise of some, these dates are two days apart.

```julia
    CE-2022-01-01 <-> ID-2022-01-01 -> Duration 2
```
