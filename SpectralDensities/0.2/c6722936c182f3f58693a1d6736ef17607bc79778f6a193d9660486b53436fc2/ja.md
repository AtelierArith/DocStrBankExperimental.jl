```
struct DebyeSD <: AbstractSD
```

DebyeSDはデバイスペクトル密度を表します。これは、結合の強さを示す振幅`α`とカットオフ周波数`ωc`によって特徴付けられます。すなわち

$$
J(\omega) = \frac{2\alpha}{\pi}\frac{\omega\omega_c^2}{\omega^2 + \omega_c^2}
$$

# フィールド

  * `α::Float64`: 結合の強さを示す振幅`α`。
  * `ωc::Float64`: カットオフ周波数。
