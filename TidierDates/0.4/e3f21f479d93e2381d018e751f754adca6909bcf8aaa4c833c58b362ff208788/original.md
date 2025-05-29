```
ymd(date_string::Union{AbstractString, Missing})
```

Converts a date string in various formats (like "yyyymmdd", "yyyy/mm/dd", "yyyy-mm-dd", or "year month day") to a Julia Date object. The function is able to handle missing values and returns missing for missing inputs.

# Arguments

date_string::Union{AbstractString, Missing}: The date string to be converted to a Date object.

# Examples

```jldoctest
julia> ymd("20201203")
2020-12-03

julia> ymd("2020/12/03")
2020-12-03

julia> ymd("2020-12-03")
2020-12-03

julia> ymd("2020 12 03")
2020-12-03

julia> ymd("2020 December 3rd")
2020-12-03

julia> ymd(missing)
missing
```
