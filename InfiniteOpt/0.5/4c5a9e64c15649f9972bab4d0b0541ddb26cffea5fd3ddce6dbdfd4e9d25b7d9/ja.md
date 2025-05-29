```
JuMP.all_variables(model::InfiniteModel, [type])::Vector{GeneralVariableRef}
```

`JuMP.all_variables` を拡張して、`model` に関連付けられたすべての変数参照のリストを返します。デフォルトでは、すべての無限、半無限、点、および有限変数が返されます。特定の型の変数を取得するには、`type` を介して具体的な変数型を指定します。型のオプションには以下が含まれます：

  * `InfiniteVariable`: すべての無限変数
  * `SemiInfiniteVariable`: すべての半無限変数
  * `PointVariable`: すべての点変数
  * `FiniteVariable`: すべての有限変数

**例**

```julia-repl
julia> all_variables(model)
4-element Array{GeneralVariableRef,1}:
 y(t)
 w(t, x)
 y(0)
 z

julia> all_variables(model, PointVariable)
1-element Array{GeneralVariableRef,1}:
 y(0)
```
