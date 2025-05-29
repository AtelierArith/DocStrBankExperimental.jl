```
plausible_limits(ds::DynamicalSystem [, idxs])
```

Return a vector of limits (min, max) for each dynamic state variable in `ds`. Optionally provide the `idxs` of the variables to use as a vector of `Symbol`s for symbolic variables present in the referrenced MTK model of `ds`.

See also [`plausible_grid`](@ref), [`plausible_ic_sampler`](@ref).
