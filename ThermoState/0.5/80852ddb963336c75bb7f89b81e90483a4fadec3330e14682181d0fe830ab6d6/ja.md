```
total_enthalpy(model,state::ThermodynamicState,unit,[options...])::Real
```

キーワードシンボル: `:total_h`

仕様を基にして、全エンタルピー (J) を計算します。

単位を必要とする場合は、関数呼び出しの前にマクロ `@to_units` を使用してください。
