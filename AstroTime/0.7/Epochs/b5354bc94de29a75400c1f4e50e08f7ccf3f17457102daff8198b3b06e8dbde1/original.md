```
from_utc(str::AbstractString, dateformat::Dates.DateFormat; scale=TAI)
from_utc(dt::Dates.DateTime; scale=TAI)
from_utc(year, month, day, hour=0, minute=0, second=0, fraction=0.0; scale=TAI)
from_utc(year, month, day, hour, minute, seconds; scale=TAI)
```

Create an `Epoch` in `scale` based on a UTC timestamp, `Dates.DateTime` or date and time components.

### Examples

```jldoctest; setup = :(using AstroTime; import Dates)
julia> from_utc(2016, 12, 31, 23, 59, 60, 0.0)
2017-01-01T00:00:36.000 TAI

julia> from_utc(2016, 12, 31, 23, 59, 60.0)
2017-01-01T00:00:36.000 TAI

julia> from_utc("2016-12-31T23:59:60.0")
2017-01-01T00:00:36.000 TAI

julia> from_utc("2016-12-31T23:59:60.0", scale=TDB)
2017-01-01T00:01:08.183 TDB
```
