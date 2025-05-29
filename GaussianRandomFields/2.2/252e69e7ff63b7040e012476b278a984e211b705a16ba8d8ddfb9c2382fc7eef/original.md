Abstract type `IsotropicCovarianceStructure <: CovarianceStructure`

# Examples

```jldoctest
julia> Exponential{Float64} <: IsotropicCovarianceStructure{Float64}
true

julia> AnisotropicExponential{Float64} <: IsotropicCovarianceStructure{Float64}
false

```

See also: [`Exponential`](@ref), [`Linear`](@ref), [`Spherical`](@ref), [`Whittle`](@ref), [`Gaussian`](@ref), [`SquaredExponential`](@ref), [`Matern`](@ref)
