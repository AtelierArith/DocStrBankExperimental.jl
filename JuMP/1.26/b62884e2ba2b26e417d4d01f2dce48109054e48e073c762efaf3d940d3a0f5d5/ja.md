```
constraint_string(
    mode::MIME,
    ref::ConstraintRef;
    in_math_mode::Bool = false,
)
```

制約 `ref` の文字列表現を、`mode` に基づいて返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @constraint(model, c, 2 * x <= 1);

julia> constraint_string(MIME("text/plain"), c)
"c : 2 x ≤ 1"
```
