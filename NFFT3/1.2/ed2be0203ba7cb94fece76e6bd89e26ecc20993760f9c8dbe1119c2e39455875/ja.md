```
nfmt_get_coefficient_array(fhat::Vector{ComplexF64},P::NFMT{D})::Array{ComplexF64} where {D}
```

は、NFMTの線形マップから返された係数ベクトルを配列に再形成します。

# 入力

  * `fhat` - フーリエ係数。
  * `P` - NFMTプラン構造。

# 参照

[`NFMT{D}`](@ref), [`nfmt_get_LinearMap`](@ref)
