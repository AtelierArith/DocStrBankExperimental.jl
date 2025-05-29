```
nfft_get_coefficient_array(fhat::Vector{ComplexF64},N::Vector{Int64})::Array{ComplexF64}
```

は、NFFTの線形マップから返された係数ベクトルを配列に再形成します。

# 入力

  * `fhat` - フーリエ係数。
  * `N` - 三角多項式 $f$ の多重バンドリミット $(N_1, N_2, \ldots, N_D)$。

# 参照

[`NFFT{D}`](@ref), [`nfft_get_LinearMap`](@ref)
