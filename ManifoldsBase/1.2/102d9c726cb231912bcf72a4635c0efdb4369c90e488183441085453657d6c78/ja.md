```
zero_vector!(M::AbstractManifold, X, p)
```

`p`において、ゼロベクトルを表す接ベクトルを接空間 $T_p\mathcal M$ から `X` に保存します。すなわち、`X` を `p` で [`AbstractManifold`](@ref) `M` にリトラクトすると `p` が得られます。
