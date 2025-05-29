```
HolidayJp
```

The `HolidayJp` module provides features for detecting holiday in Japan.

```jldoctest
julia> using Dates

julia> HolidayJp.isholiday(Date(2018, 02, 23))
false

julia> HolidayJp.isholiday(Date(2018, 12, 23))
true

julia> HolidayJp.isholiday(Date(2019, 2, 23))
true

julia> HolidayJp.isholiday(Date(2019, 12, 23))
false
```
