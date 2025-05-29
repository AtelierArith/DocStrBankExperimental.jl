```
struct VariableMin{I<:VariableId} <: AbstractUnivariateFeature
    i_variable::I
end
```

特定の変数の最小値を計算する注目すべき単変量特徴。

関連項目としては [`SoleLogics.Interval`](@ref)、[`SoleLogics.Interval2D`](@ref)、[`AbstractUnivariateFeature`](@ref)、[`VariableMax`](@ref)、[`VarFeature`](@ref)、[`AbstractFeature`](@ref) があります。
