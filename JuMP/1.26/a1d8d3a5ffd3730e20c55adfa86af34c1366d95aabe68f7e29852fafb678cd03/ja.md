```
num_variables(model::GenericModel)::Int64
```

`model`内の変数の数を返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> num_variables(model)
2
```
