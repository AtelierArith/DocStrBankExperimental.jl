```julia
iif!(M, infos, theta, beta)

```

An in-place version of [`iif`](@ref). Provides efficient computation of the item category information functions by mutating `infos` in-place, thus avoiding allocation of an intermediate arrays and output vector.

## Examples

```jldoctest
julia> beta = (a = 0.3, b = 0.1, t = (0.2, -0.5));

julia> infos = zeros(length(beta.t) + 1);

julia> iif!(GPCM, infos, 0.0, beta)
3-element Vector{Float64}:
 0.019962114838441732
 0.020570051742573044
 0.0171815514677598

julia> infos
3-element Vector{Float64}:
 0.019962114838441732
 0.020570051742573044
 0.0171815514677598
```
