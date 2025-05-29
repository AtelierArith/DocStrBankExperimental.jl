```
set_name(con_ref::ConstraintRef, s::AbstractString)
```

制約の名前属性を設定します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @constraint(model, c, [2x] in Nonnegatives())
c : [2 x] ∈ Nonnegatives()

julia> set_name(c, "my_constraint")

julia> name(c)
"my_constraint"

julia> c
my_constraint : [2 x] ∈ Nonnegatives()
```
