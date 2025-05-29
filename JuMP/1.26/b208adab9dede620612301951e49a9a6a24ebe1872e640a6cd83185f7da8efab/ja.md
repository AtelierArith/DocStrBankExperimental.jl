```
normalized_coefficient(
    constraint::ConstraintRef,
    variable::GenericVariableRef,
)
```

`constraint`内の`variable`に関連付けられた係数を返します。これは、JuMPが制約を標準形に正規化した後の値です。

関連情報は[`set_normalized_coefficient`](@ref)を参照してください。

## 例

```jldoctest; filter=r"≤|<="
julia> model = Model();

julia> @variable(model, x)
x

julia> @constraint(model, con, 2x + 3x <= 2)
con : 5 x ≤ 2

julia> normalized_coefficient(con, x)
5.0

julia> @constraint(model, con_vec, [x, 2x + 1, 3] >= 0)
con_vec : [x, 2 x + 1, 3] ∈ Nonnegatives()

julia> normalized_coefficient(con_vec, x)
2-element Vector{Tuple{Int64, Float64}}:
 (1, 1.0)
 (2, 2.0)
```
