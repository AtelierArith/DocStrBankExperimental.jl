```julia
DayOfYear(date::CDate)
```

Return the ordinal of the day in the given calendar. Also known as the 'ordinal date' relative to the epoch of the calendar. 

```julia
julia> DayOfYear(EC, 1756, 1, 27) 
```

Alternatively you can write

```julia
julia> DayOfYear("European", 1756,  1, 27) 
```

From the output we see that EC-1756-01-27 is the 27-th day  of the year 1756 in the European calendar. The same day is in the Hebrew calendar the 144-th day of the year:

`julia julia> DayOfYear(ConvertDate(EC, 1756, 1, 27, AM))`

If an error occurs 0 (representing the invalid day of the year) is returned.
