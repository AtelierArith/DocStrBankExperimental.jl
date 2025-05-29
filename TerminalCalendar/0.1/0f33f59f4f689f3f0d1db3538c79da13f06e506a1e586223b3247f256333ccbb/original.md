```
calendar(dt::Date)
```

Pretty prints the monthly calendar of `dt`.

# Example

```jldoctest
julia> calendar(Date(2021, 12))

              December 2021
┌─────┬─────┬─────┬─────┬─────┬─────┬─────┐
│ Mon │ Tue │ Wed │ Thu │ Fri │ Sat │ Sun │
├─────┼─────┼─────┼─────┼─────┼─────┼─────┤
│     │     │   1 │   2 │   3 │   4 │   5 │
│   6 │   7 │   8 │   9 │  10 │  11 │  12 │
│  13 │  14 │  15 │  16 │  17 │  18 │  19 │
│  20 │  21 │  22 │  23 │  24 │  25 │  26 │
│  27 │  28 │  29 │  30 │  31 │     │     │
└─────┴─────┴─────┴─────┴─────┴─────┴─────┘
```

```
calendar(yr::Int, mo::Int)
```

Pretty prints the monthly calendar for `yr` and `mo`.

# Example

```jldoctest
julia> calendar(2021, 12)

              December 2021
┌─────┬─────┬─────┬─────┬─────┬─────┬─────┐
│ Mon │ Tue │ Wed │ Thu │ Fri │ Sat │ Sun │
├─────┼─────┼─────┼─────┼─────┼─────┼─────┤
│     │     │   1 │   2 │   3 │   4 │   5 │
│   6 │   7 │   8 │   9 │  10 │  11 │  12 │
│  13 │  14 │  15 │  16 │  17 │  18 │  19 │
│  20 │  21 │  22 │  23 │  24 │  25 │  26 │
│  27 │  28 │  29 │  30 │  31 │     │     │
└─────┴─────┴─────┴─────┴─────┴─────┴─────┘
```

And there is more! Input different things and see what works!
