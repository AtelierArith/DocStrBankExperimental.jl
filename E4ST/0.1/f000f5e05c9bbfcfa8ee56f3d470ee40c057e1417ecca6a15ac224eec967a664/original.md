```
abstract type Container
```

Abstract type for containers that can be indexed by year and time.  i.e. `c[yr_idx, hr_idx]` will work, even if `c` contains a single number, a number for each year, a number for each hour, or a number for each year and hour.
