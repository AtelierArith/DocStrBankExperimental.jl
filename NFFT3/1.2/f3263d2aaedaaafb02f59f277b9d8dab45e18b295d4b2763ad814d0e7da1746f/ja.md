```
nfct_get_coefficient_array(fhat::Vector{Float64},N::Vector{Int64})::Array{Float64}
```

は、NFCTの線形マップから返された係数ベクトルを配列に再形成します。

# 入力

  * `fhat` - フーリエ係数。
  * `N` - 三角多項式 $f$ のマルチバンドリミット $(N_1, N_2, \ldots, N_D)$。

# 参照

[`NFCT{D}`](@ref), [`nfct_get_LinearMap`](@ref)
