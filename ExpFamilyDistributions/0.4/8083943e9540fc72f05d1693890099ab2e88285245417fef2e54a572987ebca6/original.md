```
mutable struct Dirichlet{T,D} <: δDistribution
    μ
end
```

The δ-equivalent of the [`Dirichlet`](@ref) distribution.

# Constructors

```
Dirichlet{T,D}()
Dirichlet(μ)
```

where `T` is the encoding type of the parameters and `D` is the dimension of the support and `μ` is the location of the Dirac δ pulse.

# Examples

```jldoctest
julia> δDirichlet{Float32, 2}()
δDirichlet{Float32,2}:
  μ = Float32[0.5, 0.5]

julia> δDirichlet(Float32[1/2, 1/2])
δDirichlet{Float32,2}:
  μ = Float32[0.5, 0.5]
```
