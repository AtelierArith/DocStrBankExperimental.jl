```
frac_hour(float::Number)
frac_hour(period::Type{<:Period}, float::Number)
```

Create a period in given type (defaults to `Nanosecond`) from fractional hours.

```jldoctest; output = false
using Dates
frac_hour(1+1/60) == Hour(1) + Minute(1)
# output
true
```
