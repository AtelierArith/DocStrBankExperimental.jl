StacktraceLogRecord(static*meta, runtime*meta, exception, stacktrace, data)    StacktraceLogRecord(static*meta, stacktrace, data; runtime*meta=RuntimeLogRecordMetadata(), exception=nothing)    StacktraceLogRecord(static*meta, stacktrace, args...; runtime*meta=RuntimeLogRecordMetadata(), exception=nothing)

`AbstractLogRecord` タイプで、関連するスタックトレースとオプションの例外、およびキーと値の `data` のコレクションを持ちます。

# 引数

  * `static_meta::StaticLogRecordMetadata` - 静的ログレコードメタデータ
  * `runtime_meta[_metadata]::RuntimeLogRecordMetadata` - 実行時ログレコードメタデータ
  * `exception::Union{Nothing,Exception}` - ログレコードの例外
  * `stacktrace::Base.StackTraces.StackTrace` - ログレコードのスタックトレース
  * `data::LogRecordData` - レコードに添付されたオプションの `key` => `value` ペア。提供されていない場合は `args...` から構築されます。
