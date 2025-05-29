```
shape(c::AbstractConstraint)::AbstractShape
```

制約 `c` の形状を返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> c = @constraint(model, x[2] <= 1);

julia> shape(constraint_object(c))
ScalarShape()

julia> d = @constraint(model, x in SOS1());

julia> shape(constraint_object(d))
VectorShape()
```
