Abstract type `AnisotropicCovarianceStructure <: CovarianceStructure`

# Examples

```jldoctest
julia> AnisotropicExponential{Float64} <: AnisotropicCovarianceStructure{Float64}
true

julia> Exponential{Float64} <: AnisotropicCovarianceStructure{Float64}
false

```

See also: [`AnisotropicExponential`](@ref)
