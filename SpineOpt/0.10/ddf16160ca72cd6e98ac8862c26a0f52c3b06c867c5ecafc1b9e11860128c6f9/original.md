```
t_in_t_excl(m; t_short=anything, t_long=anything)
```

Same as [t*in*t](@ref) but exclude tuples of the same `TimeSlice`.

# Keyword arguments

  * `t_short`: if given, return an `Array` of `TimeSlice`s that contain `t_short` (other than `t_short` itself).
  * `t_long`: if given, return an `Array` of `TimeSlice`s that are contained in `t_long` (other than `t_long` itself).
