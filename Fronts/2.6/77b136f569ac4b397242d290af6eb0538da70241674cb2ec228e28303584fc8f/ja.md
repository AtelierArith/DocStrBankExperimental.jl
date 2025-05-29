```
SorptivityCauchyProblem(eq::DiffusionEquation; b, S[, ob]) <: AbstractSemiinfiniteProblem{typeof(eq)}
SorptivityCauchyProblem(D; b, S[, ob]) <: AbstractSemiiinfiniteProblem{DiffusionEquation{1}}
```

境界値と吸水性が既知で初期条件が不明な半無限問題。

# 引数

  * `eq`: 支配方程式。
  * `D`: 拡散率関数。`SorptivityCauchyProblem(DiffusionEquation(D), ...)`のショートカット。

# キーワード引数

  * `b`: 課せられた境界値。
  * `S`: 規定された吸水性。
  * `ob=0`: オプションの移動境界のための境界定数。時刻`t`において、境界は`ob*√t`の位置にあります。`eq`が放射状の場合は正でなければなりません。

# 例

```jldoctest; setup = :(using Fronts)
julia> D(u) = u^4
D (generic function with 1 method)

julia> prob = Fronts.SorptivityCauchyProblem(D, b=2, S=1)
⎧ ∂u/∂t = ∂(D(u)*∂u/∂r)/∂r, r>0,t>0
⎨ u(0,t) = 2, t>0
⎩ S = 1
```

参照: [`DiffusionEquation`](@ref), [`sorptivity`](@ref)
