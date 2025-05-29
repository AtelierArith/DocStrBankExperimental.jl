```
frac_hour(float::Number)
frac_hour(period::Type{<:Period}, float::Number)
```

与えられた型（デフォルトは `Nanosecond`）から小数時間で期間を作成します。

```jldoctest; output = false
using Dates
frac_hour(1+1/60) == Hour(1) + Minute(1)
# output
true
```
