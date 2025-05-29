StacktraceLogRecord(static*meta, runtime*meta, exception, stacktrace, data)    StacktraceLogRecord(static*meta, stacktrace, data; runtime*meta=RuntimeLogRecordMetadata(), exception=nothing)    StacktraceLogRecord(static*meta, stacktrace, args...; runtime*meta=RuntimeLogRecordMetadata(), exception=nothing)

An `AbstractLogRecord` type with an associated stacktrace and optional exception and a collection of key-value `data`. 

# Arguments

  * `static_meta::StaticLogRecordMetadata` - Static log record metadata
  * `runtime_meta[_metadata]::RuntimeLogRecordMetadata` - Runtime log record metadata
  * `exception::Union{Nothing,Exception}` - Exception for log record
  * `stacktrace::Base.StackTraces.StackTrace` - Stacktrace for log record
  * `data::LogRecordData` - Optional `key` => `value` pairs attached to record. Constructed from `args...` if not provided.
