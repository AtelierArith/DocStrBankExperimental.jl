```
update!(opt_state, model_grad::Duplicated)
```

Enzymeの`Duplicated`を使用するため、これはモデル/パラメータと対応する勾配の両方を保持します。

# 例

```jldoctest
julia> using Optimisers, EnzymeCore

julia> x_dx = Duplicated(Float16[1,2,3], Float16[1,0,-4])
Duplicated{Vector{Float16}}(Float16[1.0, 2.0, 3.0], Float16[1.0, 0.0, -4.0])

julia> st = Optimisers.setup(Momentum(1/9), x_dx)  # xにのみ作用し、dxには作用しない
Leaf(Momentum(0.111111, 0.9), Float16[0.0, 0.0, 0.0])

julia> Optimisers.update!(st, x_dx)  # 両方の引数を変更する

julia> x_dx
Duplicated{Vector{Float16}}(Float16[0.8887, 2.0, 3.445], Float16[1.0, 0.0, -4.0])

julia> st
Leaf(Momentum(0.111111, 0.9), Float16[0.1111, 0.0, -0.4443])
```
