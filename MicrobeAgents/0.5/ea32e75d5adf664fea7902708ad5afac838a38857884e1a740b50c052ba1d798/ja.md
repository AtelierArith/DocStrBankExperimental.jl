```
Brumley{D} <: AbstractMicrobe{D}
```

「Brumley et al. (2019) PNAS」による化学走性細菌のモデル。このモデルは海洋細菌のシミュレーションに最適化されており、化学走性経路における（ガウス）センサーのノイズの存在を考慮しています。

デフォルトのパラメータ：

  * `motility = RunReverseFlick(0.45, [46.5], 0.45, [46.5])`
  * `state = 0.0` → 'S'
  * `rotational_diffusivity = 0.035` rad²/s
  * `memory = 1.3` s → 'τₘ'
  * `gain_receptor = 50.0` μM⁻¹ → 'κ'
  * `gain = 50.0` → 'Γ'
  * `chemotactic_precision = 6.0` → 'Π'
  * `radius = 0.5` μm → 'a'
