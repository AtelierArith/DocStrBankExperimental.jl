```
total_volume(model,state::ThermodynamicState,unit,[options...])::Real
```

キーワードシンボル: `:total_v`, `:V`

仕様を基にして、総体積 (m³) を計算します。

単位を必要とする場合は、関数呼び出しの前にマクロ `@to_units` を使用してください。
