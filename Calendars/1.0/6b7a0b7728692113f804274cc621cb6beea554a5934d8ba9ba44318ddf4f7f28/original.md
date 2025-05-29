```julia
PrintDateLine(date::CDate, io=stdout)
```

Given a `date` print a line with all representations of this date to `io`. The parts of the date can also be given separately. For example:

```julia
julia> PrintDateLine(EC, 2022, 2, 2)
```

| CE-2022-02-02 | EC-2022-02-02 | JD-2022-01-20 | AM-5782-12-01 | AH-1443-06-29 | ID-2022-05-03 | EN#0738190 | JN#2459612 |
