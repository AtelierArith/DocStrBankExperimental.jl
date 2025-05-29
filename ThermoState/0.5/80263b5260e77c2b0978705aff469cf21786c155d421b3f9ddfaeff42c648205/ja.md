```
total_helmholtz(model,state::ThermodynamicState,unit,[options...])::Real
```

キーワードシンボル: `:total_a`

仕様を基にして、全ヘルムホルツエネルギー (J) を計算します。

単位が必要な場合は、関数呼び出しの前にマクロ `@to_units` を使用してください。
