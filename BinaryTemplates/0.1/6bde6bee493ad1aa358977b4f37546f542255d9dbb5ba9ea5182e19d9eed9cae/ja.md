```
HeaderOnlyBinaryTemplate
```

ファイルの先頭に単一のチャンクで構成されるAbstractBinaryTemplate。

# フィールド

  * `expected_file_size::Int`: 期待されるファイルサイズ
  * `header::Vector{UInt8}`: テンプレートヘッダーに書き込まれるバイトのチャンク
