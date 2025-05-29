```
t_lowest_resolution_sets!(mapping)
```

Modify the given `Dict` (which must be a mapping from `TimeSlice` to `Set`) in place, so that if key `t1` is contained in key `t2`, then the former is removed and its value is merged into the latter's.
