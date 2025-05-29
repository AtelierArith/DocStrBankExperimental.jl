```
nfst_get_coefficient_array(fhat::Vector{Float64},P::NFST{D})::Array{Float64} where {D}
```

は、NFSTの線形マップから返された係数ベクトルを配列に再形成します。

# 入力

  * `fhat` - フーリエ係数。
  * `P` - NFSTプラン構造。

# 参照

[`NFST{D}`](@ref), [`nfst_get_LinearMap`](@ref)
