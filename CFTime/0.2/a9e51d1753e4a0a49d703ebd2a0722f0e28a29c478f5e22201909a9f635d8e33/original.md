```
CFTime.DateTimeProlepticGregorian(dt::AbstractString, format::AbstractString; locale="english") -> CFTime.DateTimeProlepticGregorian
```

Construct a CFTime.DateTimeProlepticGregorian by parsing the `dt` date time string following the pattern given in the `format` string.

!!! note
    This function is experimental and might be removed in the future. It relies on some internal function of `Dates` for parsing the `format`.

