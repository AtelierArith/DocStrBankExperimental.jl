```
mass_volume(model,state::ThermodynamicState,unit,[options...])::Real
```

キーワードシンボル: `:mass_v`

特定の（質量）体積 (m³/kg) を、仕様を基にして計算します。

単位を必要とする場合は、関数呼び出しの前にマクロ `@to_units` を使用してください。
