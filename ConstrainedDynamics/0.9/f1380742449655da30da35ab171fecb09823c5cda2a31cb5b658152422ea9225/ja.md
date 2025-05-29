```julia
mutable struct Mechanism{T, Nn, Ne, Nb, Nf, Ni} <: ConstrainedDynamics.AbstractMechanism{T, Nn, Ne, Nb, Nf, Ni}
```

`Mechanism` はシステムの [`Origin`](@ref)、[`Body`](@ref)s、および [`EqualityConstraint`](@ref)s を含み、シミュレーションに使用できます。

# 重要な属性

  * `origin`:        メカニズムの原点。
  * `bodies`:        メカニズムのボディ (Dict)。
  * `eqconstraints`: メカニズムの等式制約 (ジョイント) (Dict)。
  * `Δt`:            メカニズムの時間ステップ。
  * `g`:             z方向の重力加速度。

# コンストラクタ

```
Mechanism(origin, bodies; Δt, g)
Mechanism(origin, bodies, eqcs; Δt, g)
Mechanism(urdf_filename; floating, Δt, g)
```
