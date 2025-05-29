```
to_utc(ep)
to_utc(::Type{DateTime}, ep)
to_utc(::Type{Dates.DateTime}, ep)
to_utc(::Type{String}, ep, dateformat=Dates.default_format(DateTime))
```

Create a UTC timestamp or `Dates.DateTime` from an `Epoch` `ep`.

### Examples

```jldoctest; setup = :(using AstroTime; import Dates)
julia> tai = from_utc(Dates.DateTime(2018, 2, 6, 20, 45, 0, 0))
2018-02-06T20:45:37.000 TAI

julia> to_utc(tai)
"2018-02-06T20:45:00.000"

julia> to_utc(String, tai, Dates.dateformat"yyyy-mm-dd")
"2018-02-06"

julia> to_utc(Dates.DateTime, tai)
2018-02-06T20:45:00
```
