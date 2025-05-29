```
get_telemetry(source::T, start_time::DateTime, end_time::DateTime) where T<:TelemetrySource -> Vector{TelemetryPackets{T}}
```

`source`を使用して、`start_time`と`end_time`の間のテレメトリデータを取得します。

```
get_telemetry(::Type{T}, start_time::DateTime, interval) where T<:TelemetrySource -> Vector{TelemetryPackets{T}}
```

`source`を使用して、`start_time`から`start_time + interval`までのテレメトリデータを取得します。`interval`は時間単位の数値でなければなりません。以下の単位がエクスポートされています：

  * `s`は秒を表します；
  * `m`は分を表します；
  * `h`は時間を表します；
  * `d`は日を表します。

`source`が省略された場合、デフォルトのテレメトリソースが使用されます。詳細については、[`set_default_telemetry_source!`](@ref)を参照してください。

一部のソースは、この関数の簡略化されたバージョンを実装している場合もあります：

```
get_telemetry(::Type{T}) where T<:TelemetrySource -> Vector{TelemetryPackets{T}}
```

ここでは、利用可能なすべてのテレメトリが取得されます。

!!! note
    この関数から取得されたテレメトリは、デフォルトのテレメトリパケットとして選択されます。


# 戻り値

  * `Vector{TelemetryPacket{T}}`: テレメトリパケットを含むベクター。
