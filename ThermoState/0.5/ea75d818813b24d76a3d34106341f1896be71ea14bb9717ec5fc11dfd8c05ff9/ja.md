```
mass_number(model,state::ThermodynamicState,unit,[options...])::AbstractVector
```

キーワードシンボル: `:m`

提供されたシステムに存在する各化合物の質量（kg単位）を、仕様を基にして計算します。

単位が必要な場合は、関数呼び出しの前にマクロ `@to_units` を使用してください。
