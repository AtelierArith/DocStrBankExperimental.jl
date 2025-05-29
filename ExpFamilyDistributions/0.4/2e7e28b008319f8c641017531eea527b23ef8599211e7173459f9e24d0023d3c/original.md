```
mutable struct Dirichlet{T,D} <: ExpFamilyDistribution
    α
end
```

Dirichlet distribution.

# Constructors

```
Dirichlet{T,D}()
Dirichlet(α)
```

where `T` is the encoding type of the parameters and `D` is the dimension of the support and `α` is a vector of parameters.

# Examples

```jldoctest
julia> Dirichlet{Float32, 2}()
Dirichlet{Float32,2}:
  α = Float32[1.0, 1.0]

julia> Dirichlet([1.0, 2.0, 3.0])
Dirichlet{Float64,3}:
  α = [1.0, 2.0, 3.0]
```
