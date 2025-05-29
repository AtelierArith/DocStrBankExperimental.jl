```julia
isValidDate(date::CDate, warn=true)::Bool
```

Query if the given `date`` is a valid calendar date.

For example:

```julia
julia> isValidDate("Gregorian", 1756, 1, 27) 
```

Alternatively you can also write

```julia
julia> isValidDate(CE, 1756, 1, 27) 
```

This query affirms that 1756-01-27 is a valid Gregorian date.  But the next two queries return 'false' and 'true', respectively.

```julia
julia> isValidDate(CE, 1900, 2, 29)

julia> isValidDate(JD, 1900, 2, 29)
```
