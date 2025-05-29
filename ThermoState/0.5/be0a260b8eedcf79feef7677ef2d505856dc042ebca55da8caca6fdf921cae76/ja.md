```
mass_gibbs(model,state::ThermodynamicState,unit,[options...])::Real
```

キーワードシンボル: `:mass_g`

特定の（質量）ギブスエネルギー（J/kg）を、仕様を基にして計算します。

単位を必要とする場合は、関数呼び出しの前にマクロ `@to_units` を使用してください。
