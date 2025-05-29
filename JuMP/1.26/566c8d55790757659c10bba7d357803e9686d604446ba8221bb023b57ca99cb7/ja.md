```
delete(model::GenericModel, variable_refs::Vector{<:GenericVariableRef})
```

`variable_refs` に関連付けられた変数をモデル `model` から削除します。ソルバーは、単一の変数削除メソッドを繰り返し呼び出すよりも効率的な複数の変数を削除するメソッドを実装することがあります。

参照: [`unregister`](@ref)

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> delete(model, x)

julia> unregister(model, :x)

julia> print(model)
Feasibility
Subject to

julia> model[:x]
ERROR: KeyError: key :x not found
Stacktrace:
[...]
```
