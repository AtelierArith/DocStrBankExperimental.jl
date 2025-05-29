```
owner_model(v::AbstractVariableRef)
```

`v` が属するモデルを返します。

# 例

```jldoctest; setup=:(using JuMP)
julia> model = Model();

julia> x = @variable(model)
_[1]

julia> owner_model(x) === model
true
```
