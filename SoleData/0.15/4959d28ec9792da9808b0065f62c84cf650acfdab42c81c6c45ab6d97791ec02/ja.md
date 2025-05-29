```
struct VariableValue{I<:VariableId} <: AbstractUnivariateFeature
    i_variable::I
end
```

スカラー変数の値と等しい単純な特徴。

関連情報としては、[`SoleLogics.Interval`](@ref)、[`SoleLogics.Interval2D`](@ref)、[`AbstractUnivariateFeature`](@ref)、[`VarFeature`](@ref)、[`AbstractFeature`](@ref)があります。
