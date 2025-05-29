```julia
velocities(
    frame::MolecularDynamicsFiles.MDFrame
) -> Vector{StaticArraysCore.SVector{3, Float64}}

```

システム内の粒子の速度を返します。

プロパティ `:vx`, `:vy`, `:vz` に対応します。
