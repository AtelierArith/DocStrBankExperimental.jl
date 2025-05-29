```
date_to_jd(Y::Integer, M::Integer, D::Integer[, h::Integer, m::Integer, s::Number])
```

Convert a date represented using the Gregorian Calendar (Year = `y`, Month = `M` (1-12), Day = `D`, Hour = `h` (0-24), minute = `m`, and second = `s`) to Julian Day.

If the `h`, `m`, and `s` is omitted, the function assumes they are 0.

# Remarks

The algorithm was obtained from [1] (accessed on 2022-07-20).

# References

  * **[1]**: https://quasar.as.utexas.edu/BillInfo/JulianDatesG.html
