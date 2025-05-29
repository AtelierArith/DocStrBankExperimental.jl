```
JuMP.constraint_by_name(model::InfiniteModel,
                        name::String)::Union{InfOptConstraintRef, Nothing}
```

`JuMP.constraint_by_name`を拡張して、`name`に関連付けられた制約参照を返すようにします。存在しない場合は何も返しません。同じ名前を使用する制約が複数ある場合はエラーを返します。

**例**

```julia-repl
julia> constraint_by_name(model, "constr_name")
constr_name : x + pt = 3.0
```
