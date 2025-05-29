```
label(table, column)
```

`table`内の`column`の`"label"`列レベルメタデータの文字列表現を返します。このメタデータはTables.jlテーブルインターフェースと互換性がある必要があります。

`column`の`"label"`列レベルメタデータが欠落している場合は、`column`の名前を文字列として返します。

参照: [`label!`](@ref), [`labels`](@ref) ```
