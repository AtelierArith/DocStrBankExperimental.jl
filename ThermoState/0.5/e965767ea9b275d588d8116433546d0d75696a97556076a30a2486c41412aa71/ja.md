```
mol_gibbs(model,state::ThermodynamicState,unit,[options...])::Real
```

キーワードシンボル: `:mol_g`, `:g`

モルギブズエネルギー (J/mol) を、仕様を基にして計算します。

単位が必要な場合は、関数呼び出しの前にマクロ `@to_units` を使用してください。
