```
ldr(A::AbstractMatrix{T}) where {T}
```

行列 `A` に基づいて [`LDR`](@ref) 因子分解を割り当てますが、その [`LDR`](@ref) 因子分解を計算するのではなく、因子分解を単位行列に初期化します。
