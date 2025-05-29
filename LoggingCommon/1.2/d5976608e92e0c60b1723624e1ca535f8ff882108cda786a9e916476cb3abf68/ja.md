```
LogRecord(static_meta, runtime_meta, record, data)

LogRecord(static_meta, runtime_meta, record, args...)

LogRecord(static_meta, record, args...; runtime_meta=RuntimeLogRecordMetadata())
```

関連する `StaticLogRecordMetadata`、`RuntimeLogRecordMetadata`、`LogRecordData` および基になる `record` を持つログレコード。`data` が提供されていない場合、`args...` から構築されます。

# 引数

  * `static_meta::StaticLogRecordMetadata` - 静的ログレコードメタデータ
  * `runtime_meta::RuntimeLogRecordMetadata` - 実行時ログレコードメタデータ
  * `record::AbstractLogRecord` - 基になるレコード
  * `data::LogRecordData` - レコードに添付されたオプションの `key` => `value` ペア。提供されていない場合は `args...` から構築されます。
