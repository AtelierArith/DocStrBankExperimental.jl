```
JuMP.num_variables(model::InfiniteModel, [type])::Int
```

`JuMP.num_variables` を拡張して、`model` に割り当てられた `InfiniteOpt` 変数の数を返します。デフォルトでは、無限、半無限、点、および有限変数の合計数が返されます。特定のタイプの数は、`type` を介して具体的な変数タイプを指定することで取得されます。タイプのオプションには次のものが含まれます：

  * `InfiniteVariable`: すべての無限変数
  * `SemiInfiniteVariable`: すべての半無限変数
  * `PointVariable`: すべての点変数
  * `FiniteVariable`: すべての有限変数

**例**

```julia-repl
julia> num_variables(model)
3

julia> num_variables(model, InfiniteVariable)
2
```
