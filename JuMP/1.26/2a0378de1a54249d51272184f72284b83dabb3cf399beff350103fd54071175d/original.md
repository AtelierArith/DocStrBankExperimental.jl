```
model_string(mode::MIME, model::AbstractModel)
```

Return a `String` representation of `model` given the `mode`.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 0);

julia> print(model_string(MIME("text/plain"), model))
Feasibility
Subject to
 x ≥ 0
```
