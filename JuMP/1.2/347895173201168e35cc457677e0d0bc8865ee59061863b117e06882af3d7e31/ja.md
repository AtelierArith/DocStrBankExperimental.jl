```
RotatedSecondOrderCone
```

回転二次円錐オブジェクトで、ベクトル `x` のユークリッドノルムの二乗が $2tu$ 以下であるように制約をかけるために使用できます。ここで `t` と `u` は非負のスカラーです。これは `MOI.RotatedSecondOrderCone` のショートカットです。

## 例

次の制約は $\|(x-1, x-2)\|^2_2 \le 2tx$ および $t, x \ge 0$ です：

```jldoctest; setup = :(using JuMP)
julia> model = Model();

julia> @variable(model, x)
x

julia> @variable(model, t)
t

julia> @constraint(model, [t, x, x-1, x-2] in RotatedSecondOrderCone())
[t, x, x - 1, x - 2] ∈ MathOptInterface.RotatedSecondOrderCone(4)
```
