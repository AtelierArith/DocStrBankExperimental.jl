```
set_normalized_coefficients(
    con_ref::ConstraintRef,
    variable,
    new_coefficients::Vector{Tuple{Int64,T}},
)
```

`con_ref`の制約における`variable`の係数を`new_coefficients`に設定します。`new_coefficients`の各要素は、行を新しい係数にマッピングするタプルです。

このステップの前に、制約の作成中に、JuMPは同じ変数を含む複数の項を集約します。

```jldoctest; setup = :(using JuMP), filter=r"≤|<="
model = Model()
@variable(model, x)
@constraint(model, con, [2x + 3x, 4x] in MOI.Nonnegatives(2))
set_normalized_coefficients(con, x, [(1, 2.0), (2, 5.0)])
con

# output

con : [2 x, 5 x] ∈ MathOptInterface.Nonnegatives(2)
```
