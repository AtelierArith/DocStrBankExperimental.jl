```
mutable struct Gamma{T} <: ExpFamilyDistribution
    α
    β
end
```

Gamma distribution.

# Constructors

```
Gamma{T}()
Gamma{T}(α, β)
```

where `T` is the encoding type of the parameters. `α` and `β` are the parameters of the distribution.

# Examples

```jldoctest
julia> Gamma{Float32}()
Gamma{Float32}:
  α = 1.0
  β = 1.0

julia> Gamma{Float64}(1, 2)
Gamma{Float64}:
  α = 1.0
  β = 2.0
```
