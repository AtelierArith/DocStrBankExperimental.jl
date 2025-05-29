```
juldate(date::DateTime) -> reduced_julia_days
```

### Purpose

Convert from calendar to Reduced Julian Days.

### Explanation

Julian Day Number is a count of days elapsed since Greenwich mean noon on 1 January 4713 B.C.  Julian Days are the number of Julian days followed by the fraction of the day elapsed since the preceding noon.

This function takes the given `date` and returns the number of Julian calendar days since epoch `1858-11-16T12:00:00` (Reduced Julian Days = Julian Days - 2400000).

### Argument

  * `date`: date in Julian Calendar, UTC standard.  Each element can be given in `DateTime` type or anything that can be converted to that type.

### Output

The number of Reduced Julian Days is returned.

### Example

Get number of Reduced Julian Days at 2016-03-20T15:24:00.

```jldoctest
julia> using AstroLib, Dates

julia> juldate(DateTime(2016, 03, 20, 15, 24))
57468.14166666667

julia> juldate(2016, 03, 20, 15, 24)
57468.14166666667

julia> juldate("2016-03-20T15:24")
57468.14166666667
```

### Notes

Julian Calendar is assumed, thus before `1582-10-15T00:00:00` this function is *not* the inverse of `daycnv`.  For the conversion proleptic Gregorian date to number of Julian days, use `jdcnv`, which is the inverse of `daycnv`.

Code of this function is based on IDL Astronomy User's Library.
