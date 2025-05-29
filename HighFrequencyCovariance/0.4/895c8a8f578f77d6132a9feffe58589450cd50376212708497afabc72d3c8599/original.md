```
default_spacing(
    ts::SortedDataFrame;
    rough_guess_number_of_intervals::Integer = 5,
    T::Real = duration(ts; in_dates_period = false),
)
```

Calculates a default spacing between returns to use. This comes from the equation at section 1.2.3 of Zhang, Mykland, Ait-Sahalia 2005.

### Inputs

  * `ts` - The tick data.
  * `rough_guess_number_of_intervals` - A rough estimate of how many intervals to split the tick data into. This is used in a first pass to estimate the optimal interval spacing.
  * `T` - The duration of the tick data.

### Returns

  * A scalar representing the optimal interval spacing.
