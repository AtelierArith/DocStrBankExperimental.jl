```
norm(M::AbstractManifold, p, X)
```

点 `p` における接ベクトル `X` のノルムを [`AbstractManifold`](@ref) `M` から計算します。デフォルトでは、これは [`inner`](@ref) を使用して計算されます。
