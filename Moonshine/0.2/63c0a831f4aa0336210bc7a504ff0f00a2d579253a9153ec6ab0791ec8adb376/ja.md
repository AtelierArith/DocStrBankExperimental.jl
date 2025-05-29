```
CoalMutDensity
```

変異を持つ系譜の密度で、共通祖先に従います。変異は選択中立であると仮定され、すなわち共通祖先プロセスとは独立です。

関連情報として[`CoalDensity`](@ref)も参照してください。

# フィールド

  * `fC::CoalDensity`: 系譜の密度（変異を除く）
  * `Ne::BigFloat`: 有効集団サイズ
  * `μ_loc::BigFloat`: 単位座位あたりの変異率
  * `seq_length`: 配列の長さ
