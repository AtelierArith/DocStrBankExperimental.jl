```
unit!(table, column, unit)
```

`table`内の`column`に対して、`unit`の表現を`"unit"`キーの値として、`:note`スタイルの列レベルメタデータとして保存します。この`table`はTables.jlのテーブルインターフェースと互換性がある必要があります。ユーザーの便宜のために任意の値が受け入れられますが、`Unitful.Units`の単位が推奨されます。

`column`の要素タイプが`Unitful.Quantity`または`Dates.FixedPeriod`の場合、単位の設定は必要ありません（ただし、デフォルトの単位を上書きするために設定することは可能です）。

参照: [`unit`](@ref), [`units`](@ref)
