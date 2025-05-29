```
struct VariableSoftMin{T<:AbstractFloat,I<:VariableId} <: AbstractUnivariateFeature
    i_variable::I
    alpha::T
end
```

与えられた変数の最小値の「ソフト化」バージョンを計算する単変量特徴。

関連項目としては、[`SoleLogics.Interval`](@ref)、[`SoleLogics.Interval2D`](@ref)、[`AbstractUnivariateFeature`](@ref)、[`VariableMin`](@ref)、[`VarFeature`](@ref)、[`AbstractFeature`](@ref)があります。
