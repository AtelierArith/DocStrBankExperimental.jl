```
temporal_sampling(x) → symbol
```

Return the temporal sampling type of `x`, which is either an array of `Date`s or a dimensional array (with `Time` dimension).

Possible return values are:

  * `:hourly`, where the temporal difference between successive entries is exactly 1 hour.
  * `:daily`, where the temporal difference between successive entries is exactly 1 day.
  * `:monthly`, where all dates have the same day, but different month.
  * `:yearly`, where all dates have the same month and day, but different year.
  * `:other`, which means that `x` doesn't fall to any of the above categories.
