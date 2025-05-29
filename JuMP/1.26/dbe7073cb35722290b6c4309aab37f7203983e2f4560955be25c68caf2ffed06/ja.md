```
normalized_coefficient(
    constraint::ConstraintRef,
    variable_1::GenericVariableRef,
    variable_2::GenericVariableRef,
)
```

`constraint`内の`variable_1`と`variable_2`に関連する二次係数を返します。これは、JuMPが制約を標準形に正規化した後のものです。

関連情報は[`set_normalized_coefficient`](@ref)を参照してください。

## 例

```jldoctest; filter=r"≤|<="
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> @constraint(model, con, 2x[1]^2 + 3 * x[1] * x[2] + x[2] <= 2)
con : 2 x[1]² + 3 x[1]*x[2] + x[2] ≤ 2

julia> normalized_coefficient(con, x[1], x[1])
2.0

julia> normalized_coefficient(con, x[1], x[2])
3.0

julia> @constraint(model, con_vec, x.^2 <= [1, 2])
con_vec : [x[1]² - 1, x[2]² - 2] ∈ Nonpositives()

julia> normalized_coefficient(con_vec, x[1], x[1])
1-element Vector{Tuple{Int64, Float64}}:
 (1, 1.0)

julia> normalized_coefficient(con_vec, x[1], x[2])
Tuple{Int64, Float64}[]
```
