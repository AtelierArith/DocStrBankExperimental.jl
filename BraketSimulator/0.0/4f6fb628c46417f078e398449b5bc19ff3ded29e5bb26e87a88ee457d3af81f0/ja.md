```
DensityMatrixSimulator{T, S<:AbstractMatrix{T}} <: AbstractSimulator
```

密度行列の進化を表すシミュレーターで、型 `S` と要素型 `T` を持ちます。密度行列シミュレーターは、ノイズのある回路をシミュレートするために使用されるべきです。
