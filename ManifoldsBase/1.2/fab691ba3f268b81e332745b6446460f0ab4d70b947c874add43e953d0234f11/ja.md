```
copy(M::AbstractManifold, p, X)
```

点 `p` における接ベクトル `X` から [`AbstractManifold`](@ref) `M` の新しい接ベクトルに値をコピーします。新しいポイントメモリの割り当てについては [`allocate_result`](@ref) を、コピーについては [`copyto!`](@ref) を参照してください。
