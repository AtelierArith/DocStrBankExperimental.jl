```
timeagg(f, A::ClimArray, W = nothing)
```

Perform a proper temporal aggregation of the function `f` (e.g. `mean, std`) on `A` where:

  * Only full year spans of `A` are included, see [`maxyearspan`](@ref) (because most processes are affected by yearly cycle, and averaging over an uneven number of cycles typically results in artifacts)
  * Each month in `A` is weighted with its length in days (for monthly sampled data)

If you don't want these features, just do [`dropagg`](@ref)`(f, A, Time, W)`. This is also done in the case where the time sampling is unknown.

`W` are possible statistical weights that are used in conjuction to the temporal weighting, to weight each time point differently. If they are not a vector (a weight for each time point), then they have to be a dimensional array of same dimensional layout as `A` (a weight for each data point).

See also [`monthlyagg`](@ref), [`yearlyagg`](@ref), [`seasonalyagg`](@ref).

```
timeagg(f, t::Vector, x::Vector, w = nothing)
```

Same as above, but for arbitrary vector `x` accompanied by time vector `t`.
