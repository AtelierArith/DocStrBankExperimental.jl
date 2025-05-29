```
nfmt_get_coefficient_vector(fhat::Array{ComplexF64})::Vector{ComplexF64}
```

係数配列をNFMTの線形写像との乗算のためのベクトルに再形成します。

# 入力

  * `fhat` - フーリエ係数。

# 参照

[`NFMT{D}`](@ref), [`nfmt_get_LinearMap`](@ref)
