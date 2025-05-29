```
save_telemetry(tms::Vector{TelemetryPacket{T}}, prefix::String = string(T)) where T<:TelemetrySource -> Nothing
```

ベクトル `tms` にあるテレメトリをファイルに保存します。ファイル名は、`prefix` とテレメトリのタイムスタンプを組み合わせて構築されます：

```
<prefix>_<最初のテレメトリのタイムスタンプ>_<最後のテレメトリのタイムスタンプ>
```

タイムスタンプの形式は `yyyy-mm-ddTHH-MM-SS` です。`prefix` が省略された場合は、「T」が使用されます。
