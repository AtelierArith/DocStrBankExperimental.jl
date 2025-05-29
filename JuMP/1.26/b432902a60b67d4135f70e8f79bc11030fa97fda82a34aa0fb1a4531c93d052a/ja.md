```
Zeros()
```

[`MOI.Zeros`](@ref) セットの JuMP の同等物で、次元は対応する関数から推測されます。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2])
2-element Vector{VariableRef}:
 x[1]
 x[2]

julia> @constraint(model, x in Zeros())
[x[1], x[2]] ∈ Zeros()

julia> A = [1 2; 3 4];

julia> b = [5, 6];

julia> @constraint(model, A * x == b)
[x[1] + 2 x[2] - 5, 3 x[1] + 4 x[2] - 6] ∈ Zeros()
```
