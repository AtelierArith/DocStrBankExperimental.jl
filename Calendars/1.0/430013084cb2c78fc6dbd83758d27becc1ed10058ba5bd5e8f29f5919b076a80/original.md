```julia
DayNumberFromDate(date::Cdate, string::Bool, show::Bool)
```

Return the day number correspondig to the calendar date. The parts of the date can also be given separately.

If the optional parameter `string` is `true` the function returns  the day number in string format, otherwise as an integer. `string` is 'false' by default.

If the optional parameter `show` is 'true', date  and number are printed. `show` is 'false' by default.

For example:

```julia
julia> DayNumberFromDate("Gregorian", 1756, 1, 27) 
```

Using the acronym CE for 'Common Epoch' which is synonymous with 'Gregorian', this can also be written as

```julia
julia> DayNumberFromDate(CE, 1756, 1, 27) 
```

This returns the European day number 641027 as an integer by default.  If `string` is `true` the string "EN#641029" is returned. If `show`  is `true` the line "CE-1756-01-27 -> EN#641029" is printed.

If an error occurs 0 (representing the invalid day  number) is returned.
