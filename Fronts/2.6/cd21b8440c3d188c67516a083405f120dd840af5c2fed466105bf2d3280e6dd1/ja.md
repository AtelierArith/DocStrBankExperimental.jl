```
流量問題(eq::DiffusionEquation{2}; i, Qb[, angle, height, ob]) <: AbstractSemiinfiniteProblem{typeof(eq)}
```

流体の流量境界条件が課せられた半無限の放射状（極座標/円筒座標）問題。

# 引数

  * `eq`: 支配方程式。

# キーワード引数

  * `i`: 初期値。
  * `Qb`: 課せられた境界流量。
  * `angle=2π`: 領域がカバーする総角度。
  * `height=1`: 領域の高さ。
  * `ob=0`: オプションの移動境界のための境界定数。時刻 `t` において、境界は `ob*√t` の位置にあります。

# 例

```jldoctest; setup = :(using Fronts)
julia> D(u) = u^4
D (generic function with 1 method)

julia> eq = Fronts.DiffusionEquation{2}(D)
∂u/∂t = 1/r*∂(r*D(u)*∂u/∂r)/∂r

julia> prob = Fronts.FlowrateProblem(eq, i=1, Qb=1)
⎧ ∂u/∂t = 1/r*∂(r*D(u)*∂u/∂r)/∂r, r>0,t>0
⎨ u(r,0) = 1, r>0
⎩ Qb(0,t) = 1, t>0
```

参照: [`DiffusionEquation`](@ref)
