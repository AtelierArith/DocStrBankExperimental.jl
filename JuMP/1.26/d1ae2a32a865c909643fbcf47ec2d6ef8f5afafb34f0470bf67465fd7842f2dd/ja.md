```
triangle_vec(matrix::Matrix)
```

行列の上三角を、`Triangle` セットのために JuMP と MathOptInterface が要求する順序でベクトルに連結します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, X[1:3, 1:3], Symmetric);

julia> @variable(model, t)
t

julia> @constraint(model, [t; triangle_vec(X)] in MOI.RootDetConeTriangle(3))
[t, X[1,1], X[1,2], X[2,2], X[1,3], X[2,3], X[3,3]] ∈ MathOptInterface.RootDetConeTriangle(3)
```
