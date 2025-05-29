```
create_telemetry_database(label::String; kwargs...) -> TelemetryDatabase
```

`label`を持つテレメトリデータベースを作成します。

# キーワード

  * `get_telemetry_timestamp::Function`: テレメトリパケットのタイムスタンプを返す必要がある関数。APIは次のとおりです：

    `get_telemetry_timestamp(tmpacket::TelemetryPacket)::DateTime`

    （**デフォルト** = `_default_get_telemetry_timestamp`）
  * `unpack_telemetry::Function`: テレメトリフレームをアンパックした`AbstractVector{UInt8}`を返す必要がある関数で、転送関数に渡されます。フレームが無効な場合は`nothing`を返さなければなりません。関数のAPIは次のとおりです：

    `unpack_telemetry(tmpacket::TelemetryPacket)::AbstractVector{UInt8}`

    （**デフォルト** = `_default_unpack_telemetry`）
