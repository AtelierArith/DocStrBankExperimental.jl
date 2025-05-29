```
`armijo(h::Any, h_at_t::OneDAtX{S, T}; τ₀::T = T(0.01), kwargs...) where {S, T}`

Armijo基準に従ってステップサイズが許容されるかどうかを確認します。

Armijo基準: `f(x + θd) - f(x) - τ₀ θ ∇f(x+θd)d < 0`

この関数は、左辺と0の最大値を返します。

注意: `fx`、`f₀`、および`g₀`は`OneDAtX`で必要です。

関連: `wolfe`、`armijo_wolfe`、`shamanskii_stop`、`goldstein`
```
