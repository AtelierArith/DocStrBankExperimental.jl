```
keeps_filtered(f, types...) -> Bool
```

Return `true` if the following is satisfied, and `false` otherwise: Whenever the function `f` is called with arguments of types `types` and returns a single term `y`, then `linear_filter(y) == true` holds.

By default, `keeps_filtered` returns `false` for all arguments. This can be changed to avoid unneccesary (and possibly expensive) calls to `linear_filter`. Note that if `f` returns a linear combination when called with term arguments, then all terms appearing in this linear combination satisfy the condition above anyway. The setting for `keeps_filtered` doesn't matter in this case.

See also [`LinearCombinations.linear_filter`](@ref).
