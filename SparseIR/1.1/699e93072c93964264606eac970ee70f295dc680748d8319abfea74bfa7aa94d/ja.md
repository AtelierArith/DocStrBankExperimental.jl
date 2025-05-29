```
fit!(buffer::Array{S,N}, smpl::AbstractSampling, al::Array{T,N}; 
    dim=1, workarr::Vector{S}) where {S,T,N}
```

[`fit`](@ref)と同様ですが、結果を`buffer`に書き込みます。大きな一時配列を内部で割り当てないようにするには、`dim = 1`または`dim = N`を使用してください。`workarr`の長さは[`SparseIR.workarrlength`](@ref)`(smpl, al)`より小さくすることはできません。
