```
mutable struct δGamma{T} <: δDistribution
    μ
end
```

The δ-equivaltent of the [`Gamma`](@ref) distribution.

# Constructors

```
δGamma{T}()
δGamma{T}(μ)
```

where `T` is the encoding type of the parameters and `μ` is the location of the Dirac δ pulse.

# Examples

```jldoctest
julia> δGamma{Float32}()
δGamma{Float32}:
  μ = 1.0

julia> δGamma{Float64}(2)
δGamma{Float64}:
  μ = 2.0
```
