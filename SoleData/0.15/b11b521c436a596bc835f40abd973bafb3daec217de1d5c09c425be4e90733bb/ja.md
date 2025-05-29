```
struct UnivariateNamedFeature{U,I<:VariableId} <: AbstractUnivariateFeature
    i_variable::I
    name::String
end
```

名前と参照変数によってのみ識別される単変量特徴。

関連項目としては [`SoleLogics.Interval`](@ref), [`SoleLogics.Interval2D`](@ref), [`AbstractUnivariateFeature`](@ref), [`VarFeature`](@ref), [`AbstractFeature`](@ref) があります。
