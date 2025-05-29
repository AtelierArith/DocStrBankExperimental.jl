```
mdy(date_string::Union{AbstractString, Missing})
```

Converts a date string in various formats (like "mmddyyyy", "month day, year", "m/d/y", or "m-d-y") to a Julia Date object. The function is able to handle missing values and returns missing for missing inputs.

# Arguments

`date_string`::Union{AbstractString, Missing}: The date string to be converted to a Date object.

# Examples

```jldoctest
julia> mdy("12032020")
2020-12-03

julia> mdy("December 3, 2020")
2020-12-03

julia> mdy("12/03/2020")
2020-12-03

julia> mdy("12-03-2020")
2020-12-03

julia> mdy("1 24 2023")
2023-01-24

julia> mdy("01 24 2023")
2023-01-24

julia> mdy(missing)
missing

julia> mdy("FÉVRIER 20 2020") # French
2020-02-20
```
