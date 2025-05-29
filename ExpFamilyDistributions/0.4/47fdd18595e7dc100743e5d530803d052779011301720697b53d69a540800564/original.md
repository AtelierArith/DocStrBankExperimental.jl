```
mutable struct δWishart{T,D} <: δDistribution
    μ
end
```

The δ-equivaltent of the [`Wishart`](@ref) distribution.

# Constructors

```
δWishart{T,D}()
δWishart(μ)
```

where `T` is the encoding type of the parameters and `μ` is the location of the Dirac δ pulse.

# Examples

```jldoctest
julia> δWishart{Float32,2}()
δWishart{Float32,2}:
  μ = Float32[1.0 0.0; 0.0 1.0]

julia> using LinearAlgebra; δWishart(Symmetric([1 0.5; 0.5 1]))
δWishart{Float64,2}:
  μ = [1.0 0.5; 0.5 1.0]
```
