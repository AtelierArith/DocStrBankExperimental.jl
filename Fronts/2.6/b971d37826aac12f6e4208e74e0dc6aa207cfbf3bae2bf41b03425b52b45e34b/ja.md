```
ディリクレ問題(eq::DiffusionEquation; i, b[, ob]) <: AbstractSemiinfiniteProblem{typeof(eq)}
ディリクレ問題(D; i, b[, ob]) <: AbstractSemiinfiniteProblem{DiffusionEquation{1}}
```

ディリクレ境界条件を持つ半無限問題。

# 引数

  * `eq`: 支配方程式。
  * `D`: 拡散係数関数。`DirichletProblem(DiffusionEquation(D), ...)`のショートカット。

# キーワード引数

  * `i`: 初期値。
  * `b`: 課せられた境界値。
  * `ob=0`: 任意の移動境界のための境界定数。時刻`t`において、境界は`ob*√t`の位置にあります。`eq`が放射状の場合は正でなければなりません。

# 例

```jldoctest; setup = :(using Fronts)
julia> D(u) = u^4
D (generic function with 1 method)

julia> prob = Fronts.DirichletProblem(D, i=1, b=2)
⎧ ∂u/∂t = ∂(D(u)*∂u/∂r)/∂r, r>0,t>0
⎨ u(r,0) = 1, r>0
⎩ u(0,t) = 2, t>0
```

参照: [`DiffusionEquation`](@ref)
