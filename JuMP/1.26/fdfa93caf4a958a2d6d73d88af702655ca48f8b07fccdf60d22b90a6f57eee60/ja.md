```
SecondOrderCone
```

第二次の円錐オブジェクトで、ベクトル `x` のユークリッドノルムが非負スカラー `t` 以下であるように制約をかけるために使用できます。

これは [`MOI.SecondOrderCone`](@ref) セットのショートカットです。

## 例

次の制約は $\|(x-1, x-2)\|_2 \le t$ および $t \ge 0$ です：

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> @variable(model, t)
t

julia> @constraint(model, [t, x-1, x-2] in SecondOrderCone())
[t, x - 1, x - 2] ∈ MathOptInterface.SecondOrderCone(3)
```
