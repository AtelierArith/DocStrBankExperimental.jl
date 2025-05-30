```
ClassData(type, s₁, s₂, s₃)
```

入力 `type` に基づいて、サンプルサイズ `s₁`、`s₂`、`s₃` のそれぞれに対して3つの信号クラスを生成します。受け入れられる入力タイプは次のとおりです：

  * `:tri`: 長さ32の三角信号
  * `:cbf`: 長さ128のシリンダーベルファンネル信号

N. Saito と R. Coifman による「Local Discriminant Basis and their Applications」が、Journal of Mathematical Imaging and Vision, Vol. 5, 337-358 (1995) に掲載されています。

**参照:** [`generateclassdata`](@ref)
