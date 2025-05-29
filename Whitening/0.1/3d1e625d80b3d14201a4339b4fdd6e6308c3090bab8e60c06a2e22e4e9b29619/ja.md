```
ZCA(μ::AbstractVector{T}, Σ::AbstractMatrix{T}) where {T<:Base.IEEEFloat}
```

平均ベクトル `μ` ∈ ℝⁿ と共分散行列 `Σ` ∈ ℝⁿˣⁿ から ZCA トランスフォーマーを構築します。`Σ` は対称かつ正定値でなければなりません。
