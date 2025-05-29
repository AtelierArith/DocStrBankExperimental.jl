```
model_string(mode::MIME, model::AbstractModel)
```

`mode` に与えられた `model` の `String` 表現を返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 0);

julia> print(model_string(MIME("text/plain"), model))
Feasibility
Subject to
 x ≥ 0
```
