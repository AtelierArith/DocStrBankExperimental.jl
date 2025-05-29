```
function get_jacobian(
::Type{T},
system::PSY.System,
sparse_retrieve_loop::Int = 3,
) where {T <: SimulationModel}
```

システムデータから得られるシステムモデルのヤコビ行列関数を返します。

# 引数:

  * `::SimulationModel` : シミュレーションモデルのタイプ。`ResidualModel`または`MassMatrixModel`。詳細については[モデルセクション](https://nrel-sienna.github.io/PowerSimulationsDynamics.jl/stable/models/)を参照してください。
  * `system::PowerSystems.System` : システムデータ
  * `sparse_retrieve_loop::Int` : スパース性検出のためのループ数。0の場合、ヤコビ行列をDenseMatrixで構築します。
