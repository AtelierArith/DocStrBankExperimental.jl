```
PlanarVariogram(normal, data, var₁, var₂=var₁; ntol=1e-6u"m", [options])
```

変数 `var₁` と `var₂` の経験的（交差）バリオグラムを、長さ単位での平面許容値 `ntol` を持つ `normal` 方向に垂直な平面に沿って、地理空間データ `data` に格納されたデータから計算します。

`options` を基盤となる [`EmpiricalVariogram`](@ref) に渡します。
