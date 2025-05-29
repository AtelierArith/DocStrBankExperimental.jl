```
StdNames(spec = :uppersnake)
```

指定された `spec` に従って列名を標準化します。デフォルトは `:uppersnake` ケース仕様です。

# 仕様

  * `:uppersnake` - アッパースネークケース、例: COLUMN_NAME
  * `:uppercamel` - アッパーキャメルケース、例: ColumnName
  * `:upperflat` - アッパーフラットケース、例: COLUMNNAME
  * `:snake` - スネークケース、例: column_name
  * `:camel` - キャメルケース、例: columnName
  * `:flat` - フラットケース、例: columnname
