```
moles(model,state::ThermodynamicState,unit,[options...])::Real
```

キーワードシンボル: `:moles`

提供されたシステムのモルの総量（mol単位）を、仕様を基にして計算します。

単位を必要とする場合は、関数呼び出しの前にマクロ `@to_units` を使用してください。
