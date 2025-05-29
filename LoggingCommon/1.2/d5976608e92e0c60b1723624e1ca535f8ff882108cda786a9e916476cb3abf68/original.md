```
LogRecord(static_meta, runtime_meta, record, data)

LogRecord(static_meta, runtime_meta, record, args...)

LogRecord(static_meta, record, args...; runtime_meta=RuntimeLogRecordMetadata())
```

A log record with an associated `StaticLogRecordMetadata`, `RuntimeLogRecordMetadata`, `LogRecordData` and an underlying `record`. If `data` is not provided, it is constructed from `args...`. 

# Arguments

  * `static_meta::StaticLogRecordMetadata` - Static log record metadata
  * `runtime_meta::RuntimeLogRecordMetadata` - Runtime log record metadata
  * `record::AbstractLogRecord` - Underlying record
  * `data::LogRecordData` - Optional `key` => `value` pairs attached to record. Constructed from `args...` if not provided.
