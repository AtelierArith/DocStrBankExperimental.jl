```
(ls::StrongWolfe)(ϕ, dϕ, ϕdϕ, alpha0, ϕ_0, dϕ_0) -> alpha, ϕalpha
```

与えられた `ϕ(alpha::Real)`、その導関数 `dϕ`、組み合わせ評価関数 `ϕdϕ(alpha) -> (ϕ(alpha), dϕ(alpha))`、および初期推定値 `alpha0` に対して、強いウルフ条件を満たす `alpha > 0` の値を特定します。

`ϕ_0` と `dϕ_0` は、それぞれ `alpha = 0` のときの `ϕ` の値と導関数です。

`alpha` と `ϕ(alpha)` の両方が返されます。
