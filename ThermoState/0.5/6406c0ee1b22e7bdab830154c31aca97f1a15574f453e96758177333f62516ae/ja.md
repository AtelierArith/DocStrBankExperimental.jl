```
mass_entropy(model,state::ThermodynamicState,unit,[options...])::Real
```

キーワードシンボル: `:mass_s`

特定の（質量）エントロピー (J/(kg K)) を、仕様を基にして計算します。

単位を持つ単位が必要な場合は、関数呼び出しの前にマクロ `@to_units` を使用してください。
