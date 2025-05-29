```
GeoArray(A::AbstractArray{T,2|3} where T <: NumberOrMissing)
```

Construct a GeoArray from any Array. A default `AffineMap` and `CRS` will be generated.

# Examples

```julia-repl
julia> GeoArray(rand(10,10,1))
10x10x1 Array{Float64, 3} with AffineMap([1.0 0.0; 0.0 1.0], [0.0, 0.0]) and undefined CRS
```
