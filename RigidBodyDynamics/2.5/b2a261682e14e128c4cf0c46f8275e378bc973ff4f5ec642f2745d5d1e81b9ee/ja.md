```julia
velocity_to_configuration_derivative!(q̇, joint, q, v)

```

関節速度ベクトル$v$と$q$を与えられたとき、関節構成ベクトル$q$の時間微分$\dot{q}$を計算します（インプレース）。

このマッピングは線形であることに注意してください。

逆マッピングである[`configuration_derivative_to_velocity!`](@ref)も参照してください。
