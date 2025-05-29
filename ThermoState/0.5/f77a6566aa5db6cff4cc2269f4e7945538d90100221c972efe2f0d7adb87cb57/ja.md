```
mol_enthalpy(model,state::ThermodynamicState,unit,[options...])::Real
```

キーワードシンボル: `:mol_h`, `:h`

モルエンタルピー (J/mol) を、仕様を基にして計算します。

単位を必要とする場合は、関数呼び出しの前にマクロ `@to_units` を使用してください。
