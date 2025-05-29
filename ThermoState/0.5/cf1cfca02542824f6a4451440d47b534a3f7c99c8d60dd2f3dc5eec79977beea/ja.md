```
mass_helmholtz(model,state::ThermodynamicState,unit,[options...])::Real
```

キーワードシンボル: `:mass_a`

特定の（質量）ヘルムホルツエネルギー（J/kg）を、仕様を基にして計算します。

単位が必要な場合は、関数呼び出しの前にマクロ `@to_units` を使用してください。
