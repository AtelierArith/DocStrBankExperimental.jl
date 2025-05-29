```
struct VariableSoftMax{T<:AbstractFloat,I<:VariableId} <: AbstractUnivariateFeature
    i_variable::I
    alpha::T
end
```

与えられた変数の最大値の「ソフト化」バージョンを計算する単変量特徴。

関連項目としては、[`SoleLogics.Interval`](@ref)、[`SoleLogics.Interval2D`](@ref)、[`AbstractUnivariateFeature`](@ref)、[`VariableMax`](@ref)、[`VarFeature`](@ref)、[`AbstractFeature`](@ref)があります。
