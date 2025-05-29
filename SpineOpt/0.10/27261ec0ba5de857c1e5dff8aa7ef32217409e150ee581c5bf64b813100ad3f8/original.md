```
t_before_t(m; t_before=anything, t_after=anything)
```

An `Array` where each element is a `Tuple` of two *consecutive* `TimeSlice`s in model `m`, i.e., the second starting when the first ends.

# Arguments

  * `t_before`: if given, return an `Array` of `TimeSlice`s that start when `t_before` ends.
  * `t_after`: if given, return an `Array` of `TimeSlice`s that end when `t_after` starts.
