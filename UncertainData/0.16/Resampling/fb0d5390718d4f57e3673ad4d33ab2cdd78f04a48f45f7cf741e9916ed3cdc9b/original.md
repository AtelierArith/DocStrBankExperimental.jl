```
resample(x::UVAL_COLLECTION_TYPES, constraint::SamplingConstraint, n::Int) -> Vector{Vector{T}} where T
```

Resample `x` (a collection of uncertain values) once by drawing a single random number from  each of the uncertain values in `x`.

See also [`UVAL_COLLECTION_TYPES`](@ref).

## Example

```julia
# Generate some uncertain values represented by gamma distributions
uvals = [UncertainValue(Gamma(i, rand())) for i = 1:100]

# Resample the collection once 
resample(uvals)
```
