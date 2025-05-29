```
antennaArray(arysize, aryorient, dgap = Tuple(fill(Params.λ_0/2, length(arysize)));
sourceConstructer, sourceT, sourceorientlc[, orientunit=:rad, coefftype = :uniform, arycenter = zero(MVec3D{Precision.FT})])
```

提供快捷な配列構築関数。注意：ここで入力される配列および単位の向きは、指定されたオイラー角 (ZXZ) [`eulerRotationMat`](@ref) である必要があります。
