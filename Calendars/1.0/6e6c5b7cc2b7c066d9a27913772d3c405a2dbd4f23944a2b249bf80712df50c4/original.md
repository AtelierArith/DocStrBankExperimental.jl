```julia
ProfileYearAsEuropean(calendar::DPart, year::DPart, show=false)
```

Return a 4-tuple (YearStart, YearEnd, MonthsInYear, DaysInYear) as represented in the European calendar. 

Jewish New Year (Rosh HaShanah) begins the evening before the date returned. For the ISO-calendar read 'WeeksInYear' instead of 'MonthsInYear'.

Examples:

```julia
julia> ProfileYearAsEuropean(EC, 2022, true) 
julia> ProfileYearAsEuropean(CE, 2022, true) 
julia> ProfileYearAsEuropean(JD, 2022, true) 
julia> ProfileYearAsEuropean(AM, 5783, true) 
julia> ProfileYearAsEuropean(AH, 1444, true) 
julia> ProfileYearAsEuropean(ID, 2022, true) 
```

These commands return:

```julia
EC-2022 -> [EC-2022-01-01, EC-2022-12-31], 12, 365
CE-2022 -> [EC-2022-01-01, EC-2022-12-31], 12, 365
JD-2022 -> [EC-2022-01-14, EC-2023-01-13], 12, 365
AM-5783 -> [EC-2022-09-26, EC-2023-09-15], 12, 355
AH-1444 -> [EC-2022-07-30, EC-2023-07-18], 12, 354
ID-2022 -> [EC-2022-01-03, EC-2023-01-01], 52, 364
```
