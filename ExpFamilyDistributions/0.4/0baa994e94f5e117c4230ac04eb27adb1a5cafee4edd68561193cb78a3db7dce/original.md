```
mutable struct Wishart{T, D} <: ExpFamilyDistribution
    W
    v
end
```

Wishart distribution.

# Constructors

```
Wishart{T,D}()
Wishart(W[, v])
```

where `T` is the encoding type of the parameters and `W` is a [**symmetric**](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.Symmetric) DxD matrix.

# Examples

```jldoctest
julia> Wishart{Float32,2}()
Wishart{Float32,2}:
  W = Float32[1.0 0.0; 0.0 1.0]
  v = 2.0

julia> using LinearAlgebra; Wishart(Symmetric([1 0.5; 0.5 1]))
Wishart{Float64,2}:
  W = [1.0 0.5; 0.5 1.0]
  v = 2.0
```
