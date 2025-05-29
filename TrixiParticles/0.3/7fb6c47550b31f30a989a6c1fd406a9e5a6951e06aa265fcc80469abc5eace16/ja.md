```
StateEquationCole(; sound_speed, reference_density, exponent,
                  background_pressure=0.0, clip_negative_pressure=false)
```

高圧までの水の圧力と密度の関係を説明する状態方程式。

# キーワード

  * `sound_speed`:             人工音速。
  * `reference_density`:       流体の基準密度。
  * `exponent`:                大抵のシミュレーションでは `7` の値が使用される。
  * `background_pressure=0.0`: 背景圧力。
  * `clip_negative_pressure=false`: 負の圧力値は0にクリップされ、`SummationDensity`での虚偽の表面張力を防ぎますが、流体の非物理的な希薄化を許可します。
