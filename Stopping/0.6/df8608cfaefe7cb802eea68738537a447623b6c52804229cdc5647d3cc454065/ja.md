```
`goldstein(h::Any, h_at_t::OneDAtX{S, T}; τ₀::T = T(0.0001), τ₁::T = T(0.9999), kwargs...) where {S, T}`
```

ゴールドスタイン基準に従ってステップサイズが許容されるかどうかを確認します。

注意: `fx`、`f₀`、および `g₀` は `OneDAtX` に必要です。

関連情報: `armijo`、`wolfe`、`armijo_wolfe`、`shamanskii_stop`
