```
normalized_rhs(constraint::ConstraintRef)
```

`constraint`の右辺項を返します。これはJuMPが制約を正規化された形に変換した後のものです。

[`set_normalized_rhs`](@ref)も参照してください。

## 例

```jldoctest; filter=r"≤|<="
julia> model = Model();

julia> @variable(model, x);

julia> @constraint(model, con, 2x + 1 <= 2)
con : 2 x ≤ 1

julia> normalized_rhs(con)
1.0
```
