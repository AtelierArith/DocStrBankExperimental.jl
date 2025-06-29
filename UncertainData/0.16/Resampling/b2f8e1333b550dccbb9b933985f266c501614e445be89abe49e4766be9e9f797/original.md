```
resample(x::UVAL_COLLECTION_TYPES, constraint::SamplingConstraint, n::Int) -> Vector{Vector{T}} where T
```

Resample `x` (a collection of uncertain values) `n` times, applying the provided sampling `constraint`.

Returns an `n`-element vector of `length(x)`-element vectors. Each of these vectors is an independent  draw from `x`. The `i`-th element of each draw is generated by truncating the `i`-th uncertain value by  the sampling `constraint`, then drawing a single random number from the truncated value.

See also [`UVAL_COLLECTION_TYPES`](@ref).

## Example

```julia
# Generate some uncertain values where the `i`-th value is given by a normal 
# distribution with mean `i` and a standard deviation drawn from a uniform 
# distribution on `[0, 1]`.
uvals = [UncertainValue(Normal(i, rand())) for i = 1:100]

# Truncate the first 50 elements at the 90th percentile range, and the 
# last 50 elements at the 40th percentile range.
constraints = [i <= 50 ? TruncateQuantiles(0.05, 0.95) : TruncateQuantiles(0.3, 0.7) for i = 1:100]

# Truncate the distributions, then draw ten independent realisations of the collection subject
# to the provided constraints.
resample(uvals, constraints, 10)
```
