```
mutable struct δNormalDiag{T,D} <: δDistribution
    μ
end
```

The δ-equivalent of the [`NormalDiag`](@ref) distribution.

# Constructors

```
δNormalDiag{T,D}()
δNormalDiag(μ)
```

where `T` is the encoding type of the parameters, `D` is the dimension of the support and `μ` is the location of the Dirac δ pulse.

# Examples

```jldoctest
julia> δNormalDiag{Float32, 2}()
δNormalDiag{Float32,2}:
  μ = Float32[0.0, 0.0]

julia> δNormalDiag([1.0, 1.0])
δNormalDiag{Float64,2}:
  μ = [1.0, 1.0]
```
