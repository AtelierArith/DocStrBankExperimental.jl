```
VectorShape()
```

[`AbstractShape`](@ref) はベクトル値の制約を表します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> c = @constraint(model, x in SOS1());

julia> shape(constraint_object(c))
VectorShape()
```
