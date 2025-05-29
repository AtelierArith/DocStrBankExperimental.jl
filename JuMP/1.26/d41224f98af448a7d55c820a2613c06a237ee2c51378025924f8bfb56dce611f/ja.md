```
objective_function_string(mode, model::AbstractModel)::String
```

モデルの目的関数を説明する `String` を返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @objective(model, Min, 2 * x);

julia> objective_function_string(MIME("text/plain"), model)
"2 x"
```
