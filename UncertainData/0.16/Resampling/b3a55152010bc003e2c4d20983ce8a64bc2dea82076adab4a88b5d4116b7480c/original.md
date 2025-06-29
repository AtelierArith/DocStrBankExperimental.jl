```
resample(x::UVAL_COLLECTION_TYPES, constraint::Vector{<:SamplingConstraint}, n::Int) -> Vector{Vector{T}} where T
```

Resample `x` (a collection of uncertain values) `n` times, applying the provided sampling `constraint`s.

Returns an `n`-element vector of `length(x)`-element vectors. Each of these vectors is an independent  draw from `x`. The `i`-th element of each draw is generated by truncating the `i`-th uncertain value by  the `i`-th sampling `constraint`, then drawing a single random number from the truncated value.

See also [`UVAL_COLLECTION_TYPES`](@ref).

## Example

```julia
# Generate some uncertain values where the `i`-th value is given by a normal 
# distribution with mean `i` and a standard deviation drawn from a uniform 
# distribution on `[0, 1]`.
uvals = [UncertainValue(Normal(i, rand())) for i = 1:100]

# Truncate the first 50 elements at `± 0.5` standard deviations, and the 
# last 50 elements at `± 1.2` standar deviations.
constraints = [i <= 50 ? TruncateStd(0.5) : TruncateStd(1.2) for i = 1:100]

# Apply the constraints element-wise, then draw ten independent realisations 
# of the collection subject to those constraints.
resample(uvals, constraints, 10)
```
