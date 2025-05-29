```
append_builds!(config, data, existing_table_name, build_table_name)
```

`build_table_name` から `existing_table_name` に新しいビルドを追加します。ビルドテーブルの各行は、`area` および `subarea` 列を介して接続する1つ以上のバスを示す場合があります。ビルドテーブルには含まれていないが、バステーブルに含まれている既存のテーブルの任意の列については、接続されたバスの値が使用されます。
