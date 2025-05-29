```
trajectory_to_freestream(dt; kwargs...)
```

軌道パラメータを一連の時間ステップでの自由流速度パラメータに変換します（[`Freestream`](@ref）を参照）。

# 引数:

  * `dt`: 時間ステップベクトル（秒）

# キーワード引数:

  * `Xdot = zeros(length(dt))`: 各時間ステップのグローバルフレームx速度
  * `Ydot = zeros(length(dt))`: 各時間ステップのグローバルフレームy速度
  * `Zdot = zeros(length(dt))`: 各時間ステップのグローバルフレームz速度
  * `p = zeros(length(dt))`: 各時間ステップのx軸周りの角速度
  * `q = zeros(length(dt))`: 各時間ステップのy軸周りの角速度
  * `r = zeros(length(dt))`: 各時間ステップのz軸周りの角速度
  * `phi0 = 0`: 初期時間ステップのロール角
  * `theta0 = 0`: 初期時間ステップのピッチ角
  * `psi0 = 0`: 初期時間ステップのヨー角
