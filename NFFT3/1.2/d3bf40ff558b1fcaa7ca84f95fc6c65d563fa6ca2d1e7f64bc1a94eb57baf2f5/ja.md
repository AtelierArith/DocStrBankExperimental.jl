```
nfct_get_coefficient_array(fhat::Vector{Float64},P::NFCT{D})::Array{Float64} where {D}
```

は、NFCTの線形マップから返された係数ベクトルを配列に再形成します。

# 入力

  * `fhat` - フーリエ係数。
  * `P` - NFCTプラン構造。

# 参照

[`NFCT{D}`](@ref), [`nfct_get_LinearMap`](@ref)
