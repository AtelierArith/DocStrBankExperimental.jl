```
nfft_get_coefficient_array(fhat::Vector{ComplexF64},P::NFFT{D})::Array{ComplexF64} where {D}
```

は、NFFTの線形マップから返された係数ベクトルを配列に再形成します。

# 入力

  * `fhat` - フーリエ係数。
  * `P` - NFFTプラン構造。

# 参照

[`NFFT{D}`](@ref), [`nfft_get_LinearMap`](@ref)
