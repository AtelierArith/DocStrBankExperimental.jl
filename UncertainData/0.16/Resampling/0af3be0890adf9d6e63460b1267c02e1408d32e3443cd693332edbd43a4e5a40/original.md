```
resample(uvd::UVAL_COLLECTION_TYPES, n::Int) -> Vector{Vector{T}}
```

Draw `n` realisations of an uncertain value dataset according to the distributions of the uncertain values comprising it.

See also [`UVAL_COLLECTION_TYPES`](@ref). 

## Example

```julia
# Generate some uncertain values represented by gamma distributions
uvals = [UncertainValue(Gamma(i, rand())) for i = 1:100]

# Resample the collection once 
resample(uvals)
```
