```
mutable struct δNormal{T,D} <: δDistribution
    μ
end
```

The δ-equivalent of the [`Normal`](@ref) distribution.

# Constructors

```
δNormal{T,D}()
δNormal(μ)
```

where `T` is the encoding type of the parameters and `D` is the dimension of the support and `μ` is the location of the Dirac δ pulse.

# Examples

```jldoctest
julia> δNormal{Float32,2}()
δNormal{Float32,2}:
  μ = Float32[0.0, 0.0]

julia> δNormal([1.0, 1.0])
δNormal{Float64,2}:
  μ = [1.0, 1.0]
```
