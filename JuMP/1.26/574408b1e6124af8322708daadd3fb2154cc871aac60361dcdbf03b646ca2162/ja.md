```
name(con_ref::ConstraintRef)
```

制約の名前属性を取得します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @constraint(model, c, [2x] in Nonnegatives())
c : [2 x] ∈ Nonnegatives()

julia> name(c)
"c"
```
