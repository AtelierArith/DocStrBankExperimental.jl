```julia
CalendarDates(date::CDate, show::Bool)
```

Return a table of the dates of all supported calendars  corresponding to `date`. If the optional parameter `show`  is set to 'true', the date table is printed. `show` is  'false' by default.

```julia
julia> CalendarDates("Gregorian", 1756, 1, 27, true) 
```

Alternatively you can also write

```julia
julia> CalendarDates(CE, 1756, 1, 27, true) 
```

This computes a `DateTable`, which is a tuple of six calendar  dates plus the Euro day number and the Julian day number. If `show` is 'true' the table below will be printed.

```julia
    European  EC-1756-01-27
    Common    CE-1756-01-27
    Julian    JD-1756-01-16
    Hebrew    AM-5516-11-25
    Islamic   AH-1169-04-24
    IsoDate   ID-1756-05-02
    EuroNum   EN#0641029
    JulianNum JN#2362452
```
