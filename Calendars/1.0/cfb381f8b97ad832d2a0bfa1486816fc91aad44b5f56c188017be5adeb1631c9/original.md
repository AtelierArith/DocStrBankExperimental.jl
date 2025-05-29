```julia
ConvertDate(date::CDate, calendar::DPart, string::Bool, show::Bool)
```

Convert the given date to a date in the calendar `calendar`. Admissible names for the calendar are listed in the CDate docstring. 

If the optional parameter `string` is `true` the function returns the date  as a string, otherwise as an integer tuple. `string` is `false` by default.

If the optional parameter `show` is set to 'true', both dates  are printed. `show` is 'false' by default.

For example:

```julia
julia> ConvertDate(CE, 1756, 1, 27, AM) 
```

Alternatively this can also be written as

```julia
julia> ConvertDate("Gregorian", 1756, 1, 27, "Hebrew") 
```

This converts the Gregorian date (1756, 1, 27) to the Hebrew date (5516, 11, 25). By default the calendar representation (4, 5516, 11, 25) is returned.

If `string` is true the string "AM-5516-11-25" is returned. If `show` is 'true' the following line is printed:

```julia
    "CE-1756-01-27 -> AM-5516-11-25"
```

If an error occurs (0, 0, 0, 0) (representing the invalid date) is returned.
