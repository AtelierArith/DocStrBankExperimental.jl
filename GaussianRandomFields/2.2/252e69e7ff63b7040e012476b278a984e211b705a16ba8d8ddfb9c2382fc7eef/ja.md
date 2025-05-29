抽象型 `IsotropicCovarianceStructure <: CovarianceStructure`

# 例

```jldoctest
julia> Exponential{Float64} <: IsotropicCovarianceStructure{Float64}
true

julia> AnisotropicExponential{Float64} <: IsotropicCovarianceStructure{Float64}
false

```

参照: [`Exponential`](@ref), [`Linear`](@ref), [`Spherical`](@ref), [`Whittle`](@ref), [`Gaussian`](@ref), [`SquaredExponential`](@ref), [`Matern`](@ref)
