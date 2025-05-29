```julia
nanstandardize(A; dims)
```

Rescale a copy of `A` to unit variance and zero mean i.e. `(A .- nanmean(A)) ./ nanstd(A)`
