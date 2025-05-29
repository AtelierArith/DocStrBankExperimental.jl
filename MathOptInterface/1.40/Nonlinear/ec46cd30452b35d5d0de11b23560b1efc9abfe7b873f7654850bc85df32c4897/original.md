```
ConstraintIndex
```

An index to a nonlinear constraint that is returned by [`add_constraint`](@ref).

Given `data::Model` and `c::ConstraintIndex`, use `data[c]` to retrieve the corresponding [`Constraint`](@ref).
