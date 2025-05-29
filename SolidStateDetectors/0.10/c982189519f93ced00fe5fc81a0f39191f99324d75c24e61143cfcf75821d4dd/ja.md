```
apply_initial_state!(sim::Simulation{T}, ::Type{WeightingPotential}, contact_id::Int, grid::Grid{T} = Grid(sim))::Nothing
```

[`WeightingPotential`](@ref) の計算のために、`contact_id` の id を持つ [`Contact`](@ref) の初期状態を適用します。`sim.weighting_potentials[contact_id]` を [`Contact`](@ref) の固定値で上書きします。

## 引数

  * `sim::Simulation{T}`: 初期状態を適用するための [`Simulation`](@ref)。
  * `contact_id::Int`: [`WeightingPotential`](@ref) を計算するための [`Contact`](@ref) の `id`。
  * `grid::Grid{T}`: 初期状態を適用する [`Grid`](@ref)。`grid` が指定されていない場合、`sim` からデフォルトの `Grid` が決定されます。

## キーワード

  * `not_only_paint_contacts::Bool = true`: 実際にポイントがそれらの内部にあるかどうかを確認せずに、[`Contact`](@ref) の表面のペインティングアルゴリズムのみを使用するかどうか。`false` に設定するとパフォーマンスが向上しますが、[`Contact`](@ref) の内部のポイントはもはや固定されません。
  * `paint_contacts::Bool = true`: `grid` に対して [`Contact`](@ref) の表面のペインティングを有効または無効にします。

## 例

```julia
apply_initial_state!(sim, WeightingPotential, 1) # =>  id 1 の接触の重み付けポテンシャルの初期状態を適用します
```
