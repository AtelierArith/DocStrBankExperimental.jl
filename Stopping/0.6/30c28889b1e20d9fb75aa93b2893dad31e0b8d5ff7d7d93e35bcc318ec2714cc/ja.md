```
`armijo_wolfe(h::Any, h_at_t::OneDAtX{S, T}; τ₀::T = T(0.01), τ₁::T = T(0.99), kwargs...) where {S, T}`

ArmijoおよびWolfe基準に従ってステップサイズが許容されるかどうかを確認します。

注意: `fx`、`f₀`、`gx`および`g₀`は`OneDAtX`で必要です。

関連情報: `armijo`、`wolfe`、`shamanskii_stop`、`goldstein`
```
