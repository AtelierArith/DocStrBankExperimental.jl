```
push!(h::Hist2D, valx::Real, valy::Real, wgt::Real=1)
atomic_push!(h::Hist2D, valx::Real, valy::Real, wgt::Real=1)
```

Adding one value at a time into histogram. `sumw2` (sum of weights^2) accumulates `wgt^2` with a default weight of 1. `atomic_push!` is a slower version of `push!` that is thread-safe.
