```
zero_vector(M::AbstractManifold, p)
```

点 `p` における接空間 $T_p\mathcal M$ からの接ベクトルを返します。これは [`AbstractManifold`](@ref) `M` におけるゼロベクトルを表し、すなわち `p` での引き戻しが `p` を生成するようなものです。
