```
Xie{D} <: AbstractMicrobe{D}
```

「Xie et al. (2019) Biophys J」から適応された化学走性細菌のモデル。このモデルは、海洋細菌V. alginolyticusにおける化学走性応答関数の実験的測定に基づいて開発されています。このモデルの特異性は、前方および後方の泳ぎの状態に対して異なるパラメータが存在することです。

感知ノイズ（元のモデルには存在しない）は、BergとPurcellによる分子カウントノイズの公式を通じて慣習的に導入され、'Brumley et al. (2019) PNAS'に触発された`chemotactic_precision`因子を通じて調整可能です（デフォルトは0、すなわちノイズなし）。

デフォルトのパラメータ：

  * `motility`
  * `turn_rate_forward = 2.3` Hz
  * `turn_rate_backward = 1.9` Hz
  * `state = 0.0` s
  * `state_m = 0.0` s
  * `state_z = 0.0` s
  * `rotational_diffusivity = 0.26` rad²/s
  * `adaptation_time_m = 1.29` s
  * `adaptation_time_z = 0.28` s
  * `gain_forward = 2.7` 1/s
  * `gain_backward = 1.6` 1/s
  * `binding_affinity = 0.39` μM
  * `chemotactic_precision = 0.0`
  * `radius = 0.5` μm
