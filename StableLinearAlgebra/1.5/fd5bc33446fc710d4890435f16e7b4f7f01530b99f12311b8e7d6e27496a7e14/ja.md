```
ldrs(A::AbstractMatrix{T}, N::Int) where {T}
```

長さ `N` の [`LDR`](@ref) 分解のベクトルを返します。各分解は、$A$ と同じサイズの単位行列を表します。
