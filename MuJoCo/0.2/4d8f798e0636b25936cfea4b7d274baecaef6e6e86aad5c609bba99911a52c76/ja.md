```
get_physics_state(m::Model, d::Data)
```

MuJoCoモデルの状態ベクトルを抽出します。

状態ベクトルは[nq, nv, na]の次元を持つ[joint positions, joint velocities, actuator states]です。

[`mj_getState`](@ref)および[`set_physics_state!`](@ref)も参照してください。
