QuarterlyDate(d::AbstractString, format::AbstractString; locale="english") -> QuarterlyDate

Construct a Date by parsing the date string following the pattern given in the `format` string.

This method creates a `DateFormat` object each time it is called. If you are parsing many date strings of the same format, consider creating a `DateFormat` object once and using that as the second argument instead.

### Examples

```julia
julia> QuarterlyDate("1990-01", "yyy-mm")
julia> QuarterlyDate("1990-Q1", "yyy-Qq")
```
