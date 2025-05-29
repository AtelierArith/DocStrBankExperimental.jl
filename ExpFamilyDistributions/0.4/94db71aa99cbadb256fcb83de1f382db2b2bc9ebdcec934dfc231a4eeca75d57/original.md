```
mutable struct Normal{T,D} <: ExpFamilyDistribution
    μ
    Σ
end
```

Normal distribution with full covariance matrix.

# Constructors

```
Normal{T,D}()
Normal(μ[, Σ])
```

where `T` is the encoding type of the parameters, `D` is the dimension of the support, `μ` is a vector and `Σ` is a [**symmetric**](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.Symmetric) matrix.

# Examples

```jldoctest
julia> Normal{Float32,2}()
Normal{Float32,2}:
  μ = Float32[0.0, 0.0]
  Σ = Float32[1.0 0.0; 0.0 1.0]

julia> Normal([1.0, 1.0])
Normal{Float64,2}:
  μ = [1.0, 1.0]
  Σ = [1.0 0.0; 0.0 1.0]

julia> using LinearAlgebra; Normal([1.0, 1.0], Symmetric([2.0 0.5; 0.5 1.0]))
Normal{Float64,2}:
  μ = [1.0, 1.0]
  Σ = [2.0 0.5; 0.5 1.0]
```
