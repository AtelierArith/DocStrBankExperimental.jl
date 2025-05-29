抽象型 `AnisotropicCovarianceStructure <: CovarianceStructure`

# 例

```jldoctest
julia> AnisotropicExponential{Float64} <: AnisotropicCovarianceStructure{Float64}
true

julia> Exponential{Float64} <: AnisotropicCovarianceStructure{Float64}
false

```

参照: [`AnisotropicExponential`](@ref)
