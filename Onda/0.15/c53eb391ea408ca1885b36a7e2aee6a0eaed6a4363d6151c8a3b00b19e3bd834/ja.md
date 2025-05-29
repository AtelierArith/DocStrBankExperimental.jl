```
@version SignalV2 > SamplesInfoV2 begin
    recording::UUID
    file_path::(<:Any)
    file_format::String
    span::TimeSpan
    sensor_label::String
    sensor_type::String
    channels::Vector{String}
    sample_unit::String
end
```

Legolasによって生成されたレコードタイプは、[Ondaフォーマット仕様](https://github.com/beacon-biosignals/Onda.jl##ondasignal2)で説明されている`onda.signal`を表しています。

Ondaフォーマット仕様の`onda.signal@2`の必須フィールドとして文書化されているいくつかのフィールドは、このスキーマバージョンの`SamplesInfoV2`の拡張を通じてキャプチャされています。

Legolasレコードタイプに関する詳細は、https://github.com/beacon-biosignals/Legolas.jl を参照してください。
