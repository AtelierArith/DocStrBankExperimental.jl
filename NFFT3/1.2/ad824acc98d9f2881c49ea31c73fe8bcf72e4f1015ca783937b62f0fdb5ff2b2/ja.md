```
nfst_get_coefficient_vector(fhat::Array{Float64})::Vector{Float64}
```

は、NFSTの線形写像との乗算のために係数配列をベクトルに再形成します。

# 入力

  * `fhat` - フーリエ係数。

# 参照

[`NFST{D}`](@ref), [`nfst_get_LinearMap`](@ref)
