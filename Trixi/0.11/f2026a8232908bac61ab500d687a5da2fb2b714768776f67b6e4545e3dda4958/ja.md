```
AnalysisSurfaceIntegral{Variable, NBoundaries}(boundary_symbols::NTuple{NBoundaries, Symbol},
                                               variable)
```

この構造体は、特定の名前で与えられた境界/境界に関連する量 `variable` の表面積分を計算するために使用されます。たとえば、これは、境界名 `:AirfoilTop`、`:AirfoilBottom` を持つ2D翼の揚力 [`LiftCoefficientPressure2D`](@ref) または抗力係数 [`DragCoefficientPressure2D`](@ref) を計算するために使用できます。境界名は `boundary_symbols = (:AirfoilTop, :AirfoilBottom)` のように供給されます。単一の境界名も供給できます。たとえば、`boundary_symbols = (:AirfoilTop,)` のように。

  * `boundary_symbols::NTuple{NBoundaries, Symbol}`: 関心のある量が計算される境界/境界の名前
  * `variable::Variable`: 揚力や抗力のような関心のある量
