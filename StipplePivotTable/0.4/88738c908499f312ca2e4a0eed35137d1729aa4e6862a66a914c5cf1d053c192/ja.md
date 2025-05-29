```
値
```

ピボットテーブル内の値を表す可変構造体です。

# フィールド

  * `field::Union{String, Symbol}`: 値に関連付けられたフィールド名。
  * `aggregation::Union{String, Symbol}`: フィールドに適用される集計方法。
  * `formula::Union{String, Symbol, Nothing}`: 値を計算するためのオプションの数式。デフォルトは `nothing`。
  * `label::Union{String, Symbol}`: 値のラベル。デフォルトは `field` の値。
  * `format::Union{<:ValueFormatter, Nothing}`: 値のオプションのフォーマッター。デフォルトは `nothing`。
