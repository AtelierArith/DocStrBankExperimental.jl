```
nfct_get_coefficient_vector(fhat::Array{Float64})::Vector{Float64}
```

は、NFCTの線形マップとの乗算のために係数配列をベクトルに再形成します。

# 入力

  * `fhat` - フーリエ係数。

# 参照

[`NFCT{D}`](@ref), [`nfct_get_LinearMap`](@ref)
