```
ranefinfotable(ri::RanefInfo)
```

Return the information in `ri` as a column table (`NamedTuple` of `Vector`s)

The columns are

  * `name`: name of the random effect
  * `level`: level of the grouping factor
  * `cmode`: conditional mode of the random effect
  * `cstddev`: conditional standard deviation of the random effect
