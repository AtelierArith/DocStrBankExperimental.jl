```
insertcols!(gl::GridLayout, at::Integer, n::Integer; colsizes=nothing, addedcolgaps=nothing)
```

Insert `n` columns at column `at` into `GridLayout` `gl`. The new column sizes and column gaps can be optionally set with `colsizes` and `addedcolgaps` keywords. Objects spanning from at least `at-1` up to or beyond `at` are getting extended to span over the new columns. Objects from `at` and beyond are pushed back, objects before `at` are unaffected.
