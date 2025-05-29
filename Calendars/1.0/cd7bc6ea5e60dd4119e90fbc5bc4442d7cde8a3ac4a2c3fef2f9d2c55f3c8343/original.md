```julia
DateFromDayNumber(calendar::DPart, enum::DPart, string::Bool, show::Bool)
```

Return the date from a European day number expressed in the calendar.

The day number `enum` must be an integer >= 1. 

If the optional parameter `string` is `true` the function returns the date  as a string, otherwise as an integer tuple. `string` is `false` by default.

If the optional parameter `show` is set to `true`, date and number  are printed. `show` is `false` by default.

For example:

```julia
julia> DateFromDayNumber("Gregorian", 641029) 
```

Alternatively you can also write

```julia
julia> DateFromDayNumber(CE, 641029) 
```

By default this returns the calendar representation (2, 1756, 1, 27).  If `string` is true the string "CE-1756-01-27" is returned. If `show` is 'true' the line "EN#0641029 -> CE-1756-01-27"  is printed.

If an error occurs (0, 0, 0, 0) (representing the invalid date) is returned.
