```
vshbasis(Y::AbstractVSH, B::Basis, modes::Union{SphericalHarmonicModes.LM, SphericalHarmonicModes.ML}, θ, ϕ, [S = maximum(SphericalHarmonicModes.l_range(modes))])
```

有効な値の $\alpha$ に対して、すべての `(j,m)` におけるベクトル球面調和関数 $\mathbf{Y}_{j m}^\alpha(θ, ϕ)$ のセットを評価し、基底 `B` におけるその成分を返します。スカラー球面調和関数の事前割り当て済み配列 `S` を最後の引数として渡すことができます。これは [`VectorSphericalHarmonics.cache`](@ref) を使用して生成できます。
