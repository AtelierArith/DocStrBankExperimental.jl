```
MetopDiskArray(file_pointer::IOStream,
    record_layouts::Vector{FixedRecordLayout},
    field_name::Symbol; auto_convert = true) -> MetopDiskArray
```

追加フィールドを計算するMetopDiskArrayのコンストラクタ。`auto_convert = true`は、カスタム`RecordSubType`を一般的に使用されるデータ型に自動的に変換します。例えば、`VInteger`を`Float64`に変換します。
