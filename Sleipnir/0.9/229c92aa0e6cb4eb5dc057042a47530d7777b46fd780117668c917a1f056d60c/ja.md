シミュレーションで使用される物理パラメータを表す構造体。

```
PhysicalParameters{F <: AbstractFloat}
```

# フィールド

  * `ρ::F`: 氷の密度。
  * `g::F`: 重力加速度。
  * `ϵ::F`: 小さなパラメータ、しばしば摂動に使用される。
  * `η₀::F`: 初期粘度。
  * `maxA::F`: 最大A。
  * `minA::F`: 最小A。
  * `maxTlaw::F`: ある法則に従った最大温度。
  * `minTlaw::F`: ある法則に従った最小温度。
  * `noise_A_magnitude::F`: Aにおけるノイズの大きさ。
