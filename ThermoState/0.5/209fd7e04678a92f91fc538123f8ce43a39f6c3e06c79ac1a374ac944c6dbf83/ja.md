```
total_internal_energy(model,state::ThermodynamicState,unit,[options...])::Real
```

キーワードシンボル: `:total_u`

仕様を基にして、全内部エネルギー (J) を計算します。

単位が必要な場合は、関数呼び出しの前にマクロ `@to_units` を使用してください。
