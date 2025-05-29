```
EDF.PatientID
```

EDF+ ヘッダーのローカル患者識別フィールドを表す型です。

詳細については EDF+ 仕様を参照してください。

# フィールド

  * `code::Union{String,Missing}`
  * `sex::Union{Char,Missing}` (`'M'`、`'F'`、または `missing`)
  * `birthdate::Union{Date,Missing}`
  * `name::Union{String,Missing}`
