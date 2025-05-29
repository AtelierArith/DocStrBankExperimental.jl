```
copy(M::AbstractManifold, p)
```

点 `p` の値を [`AbstractManifold`](@ref) `M` から新しい点にコピーします。新しい点のメモリの割り当てについては [`allocate_result`](@ref) を、コピーについては [`copyto!`](@ref) を参照してください。
