```
ldrs!(Fs::AbstractVector{LDR{T,E}}, A::AbstractArray{T,3}, ws::LDRWorkspace{T,E}) where {T,E}
```

行列 `A[:,:,i]` のために [`LDR`](@ref) 因子分解 `Fs[i]` を計算します。
