```
antennaArray(arysize, aryorient, dgap = Tuple(fill(Params.λ_0/2, length(arysize)));
sourceConstructer, sourceT, sourceorientlc[, orientunit=:rad, coefftype = :uniform, arycenter = zero(MVec3D{Precision.FT})])
```

提供快捷的阵列构建函数。注意此处输入的阵列、单元指向必须为指定的欧拉角 (ZXZ) [`eulerRotationMat`](@ref)。
