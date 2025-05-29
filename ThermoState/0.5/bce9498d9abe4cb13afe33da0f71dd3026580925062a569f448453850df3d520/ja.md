```
temperature(model,state::ThermodynamicState,unit,[options...])::Real
```

キーワードシンボル: `:t`, `:T`

仕様を基にして温度 (K) を計算します。

単位が必要な場合は、関数呼び出しの前にマクロ `@to_units` を使用してください。
