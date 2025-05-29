```
LogicalVariable <: JuMP.AbstractVariable
```

論理変数の型で、[`Disjunction`](@ref) に関連する排他的論理に関連しています。

**フィールド**

  * `fix_value::Union{Nothing, Bool}`: 固定されたブール値がある場合。
  * `start_value::Union{Nothing, Bool}`: 初期推測がある場合。
