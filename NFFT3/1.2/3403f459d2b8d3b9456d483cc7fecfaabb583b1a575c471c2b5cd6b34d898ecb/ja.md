```
nfst_get_coefficient_array(fhat::Vector{Float64},N::Vector{Int64})::Array{Float64}
```

は、NFSTの線形写像から返された係数ベクトルを配列に再形成します。

# 入力

  * `fhat` - フーリエ係数。
  * `N` - 三角多項式 $f$ の多重バンドリミット $(N_1, N_2, \ldots, N_D)$。

# 参照

[`NFST{D}`](@ref), [`nfst_get_LinearMap`](@ref)
