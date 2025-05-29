```
t_in_t(m; t_short=anything, t_long=anything)
```

An `Array` where each element is a `Tuple` of two `TimeSlice`s in model `m`, the second containing the first.

# Keyword arguments

  * `t_short`: if given, return an `Array` of `TimeSlice`s that contain `t_short`.
  * `t_long`: if given, return an `Array` of `TimeSlice`s that are contained in `t_long`.
