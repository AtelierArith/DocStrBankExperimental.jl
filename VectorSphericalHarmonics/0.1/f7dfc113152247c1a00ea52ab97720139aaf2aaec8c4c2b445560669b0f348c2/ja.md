```
vshbasis(Y::AbstractVSH, B::Basis, j::Integer, m::Integer, n::Integer, θ, ϕ, [S = VectorSphericalHarmonics.cache(θ, ϕ, j)])
```

ベクトル球面調和関数の成分 $\mathbf{Y}_{j m}^n(θ, ϕ)$ を基底 `B` で評価します。スカラー球面調和関数の事前割り当て済み配列 `S` を最後の引数として渡すことができます。これは [`VectorSphericalHarmonics.cache`](@ref) を使用して生成できます。
