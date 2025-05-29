```
algorithm2_1!(p::Vector{T}, I::Vector{Int}, w::Vector{<:Real}) where {T<:Real}
```

`p`を、重み`w[I]`を正規化した結果の確率で埋めます。`T`は、`inv(one(T))`の結果を保持できる型でなければなりません。

参照: [`algorithm2_1`](@ref)
