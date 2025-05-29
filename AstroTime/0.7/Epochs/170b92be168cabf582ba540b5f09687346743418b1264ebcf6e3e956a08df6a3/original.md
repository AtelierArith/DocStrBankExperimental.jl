```
Epoch{S}(str[, format]) where S
```

Construct an `Epoch` with time scale `S` from a string `str`. Optionally a `format` definition can be passed as a [`DateFormat`](https://docs.julialang.org/en/stable/stdlib/Dates/#Dates.DateFormat) object or as a string. In addition to the character codes supported by `DateFormat` the code `D` can be used which is parsed as "day of year" (see the example below).  The default format is `yyyy-mm-ddTHH:MM:SS.sss`.

### Example

```jldoctest; setup = :(using AstroTime)
julia> Epoch{InternationalAtomicTime}("2018-02-06T20:45:00.0")
2018-02-06T20:45:00.000 TAI

julia> Epoch{InternationalAtomicTime}("February 6, 2018", "U d, y")
2018-02-06T00:00:00.000 TAI

julia> Epoch{InternationalAtomicTime}("2018-037T00:00", "yyyy-DDDTHH:MM")
2018-02-06T00:00:00.000 TAI
```
