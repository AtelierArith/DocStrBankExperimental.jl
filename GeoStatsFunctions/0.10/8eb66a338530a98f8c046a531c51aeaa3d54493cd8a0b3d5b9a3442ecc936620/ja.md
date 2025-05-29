```
PlanarTransiogram(normal, data, var; ntol=1e-6u"m", [options])
```

カテゴリ変数 `var` が格納された地理空間 `data` に対して、長さ単位での平面許容値 `ntol` を持つ `normal` 方向に垂直な平面に沿った経験的トランジオグラムを計算します。

`options` を基盤となる [`EmpiricalTransiogram`](@ref) に渡します。
