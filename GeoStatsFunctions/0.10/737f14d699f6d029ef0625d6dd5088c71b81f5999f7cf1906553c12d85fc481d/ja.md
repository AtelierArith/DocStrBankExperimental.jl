```
DirectionalVariogram(direction, data, var₁, var₂=var₁; dtol=1e-6u"m", [options])
```

与えられた `direction` に沿って、長さ単位でのバンドトレランス `dtol` を持つ地理空間 `data` に格納された変数 `var₁` と `var₂` の経験的（クロス）バリオグラムを計算します。

`options` を基盤となる [`EmpiricalVariogram`](@ref) に渡します。
