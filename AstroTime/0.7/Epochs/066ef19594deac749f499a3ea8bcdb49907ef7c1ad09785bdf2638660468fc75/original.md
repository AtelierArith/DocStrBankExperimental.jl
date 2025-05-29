```
Epoch(str[, format])
```

Construct an `Epoch` from a string `str`. Optionally a `format` definition can be passed as a [`DateFormat`](https://docs.julialang.org/en/stable/stdlib/Dates/#Dates.DateFormat) object or as a string. In addition to the character codes supported by `DateFormat` the character code `D` is supported which is parsed as "day of year" (see the example below) and the character code `t` which is parsed as the time scale.  The default format is `yyyy-mm-ddTHH:MM:SS.sss ttt`.

**Note:** Please be aware that this constructor requires that the time scale is part of `str`, e.g. `2018-02-06T00:00 TAI`. Otherwise use an explicit constructor, e.g. `Epoch{TAI}`.

### Example

```jldoctest; setup = :(using AstroTime)
julia> Epoch("2018-02-06T20:45:00.0 TAI")
2018-02-06T20:45:00.000 TAI

julia> Epoch("2018-037T00:00 TAI", "yyyy-DDDTHH:MM ttt")
2018-02-06T00:00:00.000 TAI
```
