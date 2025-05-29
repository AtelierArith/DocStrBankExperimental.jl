```
StateEquationIdealGas( ;sound_speed, reference_density, gamma, background_pressure=0.0,
                       clip_negative_pressure=false)
```

理想気体の法則を使用して、気体の圧力と密度の関係を説明する状態方程式。

# キーワード

  * `sound_speed`                 : 人工音速。
  * `reference_density`           : 流体の基準密度。
  * `gamma`                       : 熱容量比
  * `background_pressure=0.0`     : 背景圧力。
  * `clip_negative_pressure=false`: 負の圧力値は0にクリップされ、`SummationDensity`とのスプリアスな表面張力を防ぎますが、流体の非物理的な希薄化を許可します。
