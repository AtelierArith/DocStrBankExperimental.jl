```
nfft_get_coefficient_vector(fhat::Array{ComplexF64})::Vector{ComplexF64}
```

は、NFFTの線形写像との乗算のために係数配列をベクトルに再形成します。

# 入力

  * `fhat` - フーリエ係数。

# 参照

[`NFFT{D}`](@ref), [`nfft_get_LinearMap`](@ref)
