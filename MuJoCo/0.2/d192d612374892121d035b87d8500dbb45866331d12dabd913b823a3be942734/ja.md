```
set_physics_state!(m::Model, d::Data, x::AbstractVector)
```

MuJoCoモデルの状態ベクトルを設定します。

状態ベクトルは、次の次元を持つ[joint positions, joint velocities, actuator states]で構成されています(nq, nv, na)。状態を設定した後は、[`forward!`](@ref)を呼び出して、新しい状態に従って`Data`オブジェクト内のすべての導出量を計算します。

他に[`mj_setState`](@ref)および[`get_physics_state`](@ref)も参照してください。
