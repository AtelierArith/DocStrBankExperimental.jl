```
CauchyProblem(eq::DiffusionEquation; b, d_dob[, ob]) <: AbstractSemiinfiniteProblem{typeof(eq)}
CauchyProblem(D; b, d_dob[, ob]) <: AbstractSemiinfiniteProblem{DiffusionEquation{1}}
```

初期境界条件（および未知の初期条件）を持つ半無限問題。

# 引数

  * `eq`: 支配方程式。
  * `D`: 拡散率関数。`CauchyProblem(DiffusionEquation(D), ...)`のショートカット。

# キーワード引数

  * `b`: 課せられた境界値。
  * `d_dob`: 境界での解の`o`-導関数の課せられた値。ここで、`o`はボルツマン変数です。

この値は、任意の時間`t>0`において`√t*d_dr(<solution>, :b, t)`に相当します。

  * `ob=0`: オプションの移動境界のための境界定数。時間`t`において、境界は`ob*√t`の位置にあります。`eq`が放射状の場合は正でなければなりません。

# 例

```jldoctest; setup = :(using Fronts)
julia> D(u) = u^4
D (generic function with 1 method)

julia> prob = Fronts.CauchyProblem(D, b=2, d_dob=-0.1)
⎧ ∂u/∂t = ∂(D(u)*∂u/∂r)/∂r, r>0,t>0
⎨ u(0,t) = 2, t>0
⎩ √t*∂u/∂r(0,t) = -0.1, t>0
```

参照: [`DiffusionEquation`](@ref)
