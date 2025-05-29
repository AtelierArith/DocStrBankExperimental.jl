```
ldrs(A::AbstractArray{T,3}, ws::LDRWorkspace{T,E}) where {T,E}
```

`size(A, 3)`の長さを持つ[`LDR`](@ref)因子分解のベクトルを返します。ここで、各行列`A[:,:,i]`に対して[`LDR`](@ref)因子分解があります。
