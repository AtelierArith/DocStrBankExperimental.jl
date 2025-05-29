```
Celani{D} <: AbstractMicrobe{D}
```

「Celani and Vergassola (2010) PNAS」からの応答カーネルを使用した化学走性細菌のモデルで、E. coliに関する実験から抽出されています。

感知ノイズ（元のモデルには存在しない）は、BergとPurcellによる分子カウントノイズの公式を通じて慣習的に導入され、'Brumley et al. (2019) PNAS'に触発された`chemotactic_precision`因子を通じて調整可能です（デフォルトは0、すなわちノイズなし）。

デフォルトのパラメータ：

  * `motility = RunTumble(0.67, [30.0], Isotropic(D), 0.1)`
  * `state = 0`
  * `rotational_diffusivity = 0.26` rad²/s
  * `gain = 50.0`
  * `memory = 1` s
  * `radius = 0.5` μm
