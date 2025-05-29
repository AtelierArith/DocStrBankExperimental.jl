```
vshbasis(Y::AbstractVSH, B::Basis, j::Integer, m::Integer, θ, ϕ, [S = VectorSphericalHarmonics.cache(θ, ϕ, j)])
```

有効な値の $\alpha$ に対してベクトル球面調和関数 $\mathbf{Y}_{j m}^\alpha(θ, ϕ)$ のセットを評価し、基底 `B` におけるその成分を返します。スカラー球面調和関数の事前割り当て済み配列 `S` を最後の引数として渡すことができます。これは [`VectorSphericalHarmonics.cache`](@ref) を使用して生成できます。
