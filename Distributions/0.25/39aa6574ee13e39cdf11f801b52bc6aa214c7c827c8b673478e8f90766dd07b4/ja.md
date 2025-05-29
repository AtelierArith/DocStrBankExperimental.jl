```
params!{D<:AbstractMvLogNormal}(::Type{D},m::AbstractVector,S::AbstractMatrix,μ::AbstractVector,Σ::AbstractMatrix)
```

与えられた平均と共分散に対して (スケール, ロケーション) を計算し、結果を `μ` と `Σ` に格納します。
