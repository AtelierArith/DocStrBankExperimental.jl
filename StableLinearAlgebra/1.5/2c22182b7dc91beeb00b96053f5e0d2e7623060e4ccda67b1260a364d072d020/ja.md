```
ldrs(A::AbstractMatrix{T}, N::Int, ws::LDRWorkspace{T,E}) where {T,E}
```

行列 `A` を表す長さ `N` の [`LDR`](@ref) 分解のベクトルを返します。
