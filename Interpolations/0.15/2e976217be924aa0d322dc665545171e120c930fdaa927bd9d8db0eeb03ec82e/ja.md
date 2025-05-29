```
itp = interpolate(A, interpmode)
```

配列 `A` を `interpmode` によって決定されたモードで補間します。`interpmode` は次のいずれかである可能性があります。

  * `NoInterp()`
  * `BSpline(Constant())`
  * `BSpline(Linear())`
  * `BSpline(Quadratic(bc))` (見てください [`BoundaryCondition`](@ref))
  * `BSpline(Cubic(bc))`

異なる補間スキームを各軸に沿って使用したい場合は、そのような値のタプルであることもできます。
