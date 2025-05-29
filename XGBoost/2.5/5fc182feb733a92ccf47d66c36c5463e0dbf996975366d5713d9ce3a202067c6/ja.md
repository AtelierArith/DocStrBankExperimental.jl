```
update!(b::Booster, data; num_round=1, kw...)
update!(b::Booster, data, ℓ′, ℓ″; kw...)
```

[`Booster`](@ref) `b` に対して `num_round` 回の勾配ブースティングを実行します。

カスタム損失のために損失関数の1階および2階導関数（それぞれ `ℓ′` と `ℓ″`）を提供することができます。
