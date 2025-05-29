```
push!(h::Hist1D, val::Real, wgt::Real=1)
atomic_push!(h::Hist1D, val::Real, wgt::Real=1)
```

Adding one value at a time into histogram. `sumw2` (sum of weights^2) accumulates `wgt^2` with a default weight of 1. `atomic_push!` is a slower version of `push!` that is thread-safe.

N.B. To append multiple values at once, use broadcasting via `push!.(h, [-3.0, -2.9, -2.8])` or `push!.(h, [-3.0, -2.9, -2.8], 2.0)`
