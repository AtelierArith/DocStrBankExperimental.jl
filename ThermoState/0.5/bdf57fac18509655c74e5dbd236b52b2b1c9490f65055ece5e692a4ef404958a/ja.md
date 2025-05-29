```
total_entropy(model,state::ThermodynamicState,unit,[options...])::Real
```

キーワードシンボル: `:total_s`

仕様を基にして、全エントロピー (J/K) を計算します。

単位が必要な場合は、関数呼び出しの前にマクロ `@to_units` を使用してください。
