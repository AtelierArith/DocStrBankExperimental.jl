```
struct TelemetryPacket{T <: TelemetrySource}
```

ソース `T` から取得したテレメトリパケット。

# フィールド

  * `timestamp::DateTime`: テレメトリパケットのタイムスタンプ。
  * `data::Vector{UInt8}`: `UInt8` のベクターにカプセル化されたテレメトリデータ。
  * `metadata::Dict{String, Any}`: テレメトリパケットに関するメタデータを保持するための辞書。
