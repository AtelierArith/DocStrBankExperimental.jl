```
interpolate_nans(grid, x, intp::Linear, extr::BoundaryCondition)
```

提供された `grid` に対して、`NaN` 値を持つ可能性のある `x` を線形補間します。

`x` の端に `NaN` がある場合、`extrapolation_bc` 境界条件が適用されます（詳細については `Interpolations.BoundaryCondition` のドキュメントを参照してください）。境界条件のデフォルトは `NaN` であり、これにより `x` の端にある `NaN` 値は補間されません。`Flat(gt)` や `Line(gt)` のような他の境界条件も、`gt = OnCell()` または `gt = OnGrid()` とともに機能します。
