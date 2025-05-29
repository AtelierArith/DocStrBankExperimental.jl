```
Tenor(x:: AbstractString)
```

Constructor for creating a Tenor object from a string. The input string must start with the multiplier as Integer followed by the unit (as last character).

Example:

```
julia> Tenor.(("1D", "3W", "1M", "10y"))
(Tenor(TDays, 1), Tenor(TWeeks, 3), Tenor(TMonths, 1), Tenor(TYears, 10))
```
