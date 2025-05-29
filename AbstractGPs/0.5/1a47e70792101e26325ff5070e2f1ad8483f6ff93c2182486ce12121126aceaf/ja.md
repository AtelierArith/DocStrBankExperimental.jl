```
posterior(fx::FiniteGP, y::AbstractVector{<:Real})
```

観測値 `y` が `fx.x` で行われ、ノイズ `fx.Σy` の下で得られたときの `fx.f` に対する事後分布を構築します。これは別の `AbstractGP` オブジェクトです。GPにおける正確な推論の要約については、[1] の第2章を参照してください。この事後過程の平均関数は

```julia
m_posterior(x) = m(x) + k(x, fx.x) inv(cov(fx)) (y - mean(fx))
```

およびカーネルは

```julia
k_posterior(x, z) = k(x, z) - k(x, fx.x) inv(cov(fx)) k(fx.x, z)
```

であり、ここで `m` と `k` はそれぞれ `fx.f` の平均関数とカーネルです。
