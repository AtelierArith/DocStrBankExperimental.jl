```
@version PlanV4 begin
    # EDF.SignalHeader フィールド
    label::String
    transducer_type::String
    physical_dimension::String
    physical_minimum::Float32
    physical_maximum::Float32
    digital_minimum::Float32
    digital_maximum::Float32
    prefilter::String
    samples_per_record::Int32
    # EDF.FileHeader フィールド
    seconds_per_record::Float64
    # Onda.SignalV4 フィールド (channels -> channel)、欠落している可能性あり
    sensor_type::Union{Missing,AbstractString}
    channel::Union{Missing,AbstractString}
    sample_unit::Union{Missing,AbstractString}
    sample_resolution_in_unit::Union{Missing,Float64}
    sample_offset_in_unit::Union{Missing,Float64}
    sample_type::Union{Missing,AbstractString}
    sample_rate::Union{Missing,Float64}
    # エラー、エラーがないことを示すには `nothing` を使用
    error::Union{Nothing,String}
end
```

Legolas によって生成されたレコードタイプは、単一の EDF 信号から Onda チャンネルへの変換を説明しています。 列は次のものの組み合わせです。

  * `EDF.SignalHeader` からのフィールド (すべて必須)
  * `EDF.FileHeader` からの `seconds_per_record` フィールド (必須)
  * `Onda.SignalV4` からのフィールド (オプション、変換に失敗したことを示すために `missing` になる可能性あり)、`file_path` を除く
  * `error` は、変換が成功しているか、成功することが期待される場合は `nothing` であり、キャッチされたエラーの場合はエラーの原因を説明する `String` (バックトレース付き) です。
