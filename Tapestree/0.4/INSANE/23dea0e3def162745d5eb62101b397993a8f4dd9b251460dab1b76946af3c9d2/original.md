```
time_rate(tree::T, f::Function, δt::Float64) where {T <: iT}
```

Extract values from `f` function at times sampled every `δt` across the tree.
