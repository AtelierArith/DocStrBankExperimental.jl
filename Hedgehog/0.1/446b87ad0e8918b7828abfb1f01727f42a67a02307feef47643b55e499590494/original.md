```
to_ticks(x::Date)
```

Convert a `Date` to milliseconds since the Julia `Dates` module epoch (0000-01-01).

Note: This is calculated by converting the `Date` to days since epoch  (`Dates.date2epochdays`) and multiplying by `MILLISECONDS_IN_DAY`.
