```
mass(model,state::ThermodynamicState,unit,[options...])::Real
```

キーワードシンボル: `:mass`

提供されたシステムの総質量（kg単位）を、仕様を基にして計算します。

単位を持つ単位が必要な場合は、関数呼び出しの前にマクロ `@to_units` を使用してください。
