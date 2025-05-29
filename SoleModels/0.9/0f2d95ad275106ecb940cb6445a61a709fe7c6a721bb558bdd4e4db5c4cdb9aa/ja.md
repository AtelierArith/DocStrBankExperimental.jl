```
defaultconsequent(m::DecisionList)
```

`m` のデフォルト [`consequent`](@ref) を返します。

!!! note
    返されるモデルは、`m` が完全である場合に限り完全です。詳細は [`iscomplete`](@ref) を参照してください。


他に [`AbstractModel`](@ref)、[`DecisionList`](@ref)、[`Rule`](@ref) を参照してください。
