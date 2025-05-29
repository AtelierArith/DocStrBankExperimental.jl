```
apply_initial_state!(sim::Simulation{T}, ::Type{ElectricPotential}, grid::Grid{T} = Grid(sim);
        not_only_paint_contacts::Bool = true, paint_contacts::Bool = true)::Nothing where {T <: SSDFloat}
```

初期状態を計算のために適用します [`ElectricPotential`](@ref)。`sim.electric_potential`、`sim.q_eff_imp`、`sim.q_eff_fix`、`sim.ϵ` および `sim.point_types` を `sim.detector` で定義された材料特性と固定ポテンシャルで上書きします。

## 引数

  * `sim::Simulation{T}`: 初期状態を適用するための [`Simulation`](@ref)。
  * `grid::Grid{T}`: 初期状態を適用する [`Grid`](@ref)。`grid` が指定されていない場合、`sim` からデフォルトの `Grid` が決定されます。

## キーワード

  * `not_only_paint_contacts::Bool = true`: [`Contact`](@ref) の表面のペインティングアルゴリズムのみを使用するかどうか、実際にポイントが内部にあるかどうかを確認せずに。`false` に設定するとパフォーマンスが向上しますが、[`Contact`](@ref) 内のポイントはもはや固定されません。
  * `paint_contacts::Bool = true`: `grid` に対して [`Contact`](@ref) の表面のペインティングを有効または無効にします。

## 例

```julia
apply_initial_state!(sim, ElectricPotential, paint_contacts = false)
```
