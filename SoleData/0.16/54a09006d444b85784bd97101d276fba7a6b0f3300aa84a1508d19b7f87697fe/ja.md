```
struct VariableValue{I<:VariableId, N<:Union{VariableName, Nothing}} <: AbstractUnivariateFeature
    i_variable::I
    i_name::N
end
```

スカラー変数の値と、オプションでその名前に等しい単純な特徴。

関連情報としては、[`SoleLogics.Interval`](@ref)、[`SoleLogics.Interval2D`](@ref)、[`AbstractUnivariateFeature`](@ref)、[`VarFeature`](@ref)、[`AbstractFeature`](@ref)があります。
