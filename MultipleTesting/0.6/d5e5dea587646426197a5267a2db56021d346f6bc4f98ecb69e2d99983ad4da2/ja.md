```
adjust(PValues, <:PValueAdjustment)
adjust(PValues, Int, <:PValueAdjustment)
```

p値の調整

# 例

```jldoctest
julia> pvals = PValues([0.001, 0.01, 0.03, 0.5]);

julia> adjust(pvals, BenjaminiHochberg())
4-element Array{Float64,1}:
 0.004
 0.02
 0.039999999999999994
 0.5

julia> adjust(pvals, 6, BenjaminiHochberg()) # 6のうち4つのp値
4-element Array{Float64,1}:
 0.006
 0.03
 0.06
 0.75

julia> adjust(pvals, BarberCandes())
4-element Array{Float64,1}:
 0.3333333333333333
 0.3333333333333333
 0.3333333333333333
 1.0
```

# 参照

`PValueAdjustment`s:

[`Bonferroni`](@ref) [`BenjaminiHochberg`](@ref) [`BenjaminiHochbergAdaptive`](@ref) [`BenjaminiYekutieli`](@ref) [`BenjaminiLiu`](@ref) [`Hochberg`](@ref) [`Holm`](@ref) [`Hommel`](@ref) [`Sidak`](@ref) [`ForwardStop`](@ref) [`BarberCandes`](@ref)
