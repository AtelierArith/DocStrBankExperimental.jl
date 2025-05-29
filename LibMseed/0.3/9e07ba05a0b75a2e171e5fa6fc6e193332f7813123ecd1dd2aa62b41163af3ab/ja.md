```
MseedTraceID
```

単一チャネルの連続データのいくつかのセグメントのコンテナ。

# フィールド

  * `id`: 'URN'としてのソースチャネルIDを説明する`String`。
  * `earliest::NanosecondDateTime`: すべてのセグメントにおける最も早いサンプルの時間。
  * `latest::NanosecondDateTime`: すべてのセグメントにおける最も遅いサンプルの時間。
  * `segments::Vector{MseedTraceSegment}`: データセグメントのセット。各セグメントは同じデータ型でなければならない。
