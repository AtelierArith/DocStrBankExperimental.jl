```
mass_internal_energy(model,state::ThermodynamicState,unit,[options...])::Real
```

キーワードシンボル: `:mass_u`

仕様を基にして、特定の（質量）内部エネルギー（J/kg）を計算します。

単位を必要とする場合は、関数呼び出しの前にマクロ `@to_units` を使用してください。
