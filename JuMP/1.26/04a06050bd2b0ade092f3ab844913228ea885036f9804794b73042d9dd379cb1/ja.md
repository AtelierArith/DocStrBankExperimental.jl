```
is_valid(model::GenericModel, con_ref::ConstraintRef{<:AbstractModel})
```

`model`内の有効な制約を参照している場合、`true`を返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @constraint(model, c, 2 * x <= 1);

julia> is_valid(model, c)
true

julia> model_2 = Model();

julia> is_valid(model_2, c)
false
```
