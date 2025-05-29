```
struct VariableMax{I<:VariableId} <: AbstractUnivariateFeature
    i_variable::I
end
```

特定の変数の最大値を計算する注目すべき単変量特徴。

関連項目としては、[`SoleLogics.Interval`](@ref)、[`SoleLogics.Interval2D`](@ref)、[`AbstractUnivariateFeature`](@ref)、[`VariableMin`](@ref)、[`VarFeature`](@ref)、[`AbstractFeature`](@ref)があります。
