```
constraints_string(mode, model::AbstractModel)::Vector{String}
```

モデルの各制約を説明する`String`のリストを返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 0);

julia> @constraint(model, c, 2 * x <= 1);

julia> constraints_string(MIME("text/plain"), model)
2-element Vector{String}:
 "c : 2 x ≤ 1"
 "x ≥ 0"
```
