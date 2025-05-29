```
EDF.read!(file::File)
```

`file.io` からすべての EDF サンプルおよび注釈データを `file.signals` と `file.annotations` に読み込み、`file` を返します。`eof(file.io)` の場合、`file` は変更されずに返されます。
