```julia
configuration_derivative_to_velocity!(v, joint, q, q̇)

```

関節構成ベクトル$q$とその時間微分$\dot{q}$から関節速度ベクトル$v$を計算します（インプレース）。

このマッピングは線形であることに注意してください。

逆マッピングである[`velocity_to_configuration_derivative!`](@ref)も参照してください。
