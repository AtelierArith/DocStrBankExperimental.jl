```
SurfaceTensionAkinci(surface_tension_coefficient=1.0)
```

Akinci [Akinci2013](@cite) によって概説された原則を基に、表面張力と接着効果のモデルを実装します。このモデルは、粒子間力を利用して、液体表面の微妙な挙動、例えば液滴の形成や合体・分離の動態を捉えるのに重要です。

詳細については [`surface_tension`](@ref) を参照してください。

# キーワード

  * `surface_tension_coefficient=1.0`: 表面張力の力の大きさを調整するためのパラメータで、シミュレーションにおける表面張力現象の表現を微調整するのに役立ちます。
