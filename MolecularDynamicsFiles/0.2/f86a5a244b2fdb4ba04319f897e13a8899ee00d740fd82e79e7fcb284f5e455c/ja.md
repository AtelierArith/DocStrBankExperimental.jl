```julia
SimulationBox(
    basis::AbstractMatrix{Float64},
    origin::AbstractVector{Float64},
    bc::MolecularDynamicsFiles.BoundaryConditions,
    istriclinic::Bool
) -> MolecularDynamicsFiles.SimulationBox

```

シミュレーションボックスを構築します。 `basis` は列にシミュレーションボックスベクトルを持つ3x3行列です。 `origin` は3成分のベクトルです。
