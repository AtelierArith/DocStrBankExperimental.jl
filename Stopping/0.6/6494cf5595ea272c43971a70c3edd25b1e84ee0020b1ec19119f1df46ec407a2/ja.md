```
`wolfe(h::Any, h_at_t::OneDAtX{S, T}; τ₁::T = T(0.99), kwargs...) where {S, T}`
```

ウルフ基準に従ってステップサイズが許容されるかどうかを確認します。

強ウルフ基準: `|∇f(x+θd)| - τ₁||∇f(x)|| < 0`。

この関数は左辺と0の最大値を返します。

注意: `gx` と `g₀` は `OneDAtX` に必要です。

関連: `armijo`, `armijo_wolfe`, `shamanskii_stop`, `goldstein`
