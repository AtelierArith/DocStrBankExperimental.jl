```
@version SamplesInfoV2 begin
    sensor_type::String
    channels::Vector{String}
    sample_unit::String
    sample_resolution_in_unit::Float64
    sample_offset_in_unit::Float64
    sample_type::String = onda_sample_type_from_julia_type(sample_type)
    sample_rate::Float64
end
```

信号のサンプルデータに固有の `onda.signal` フィールドのバンドルを表す Legolas 生成のレコードタイプであり、外部のファイルや記録情報は省略されています。これは、後者の情報が無関係であるか、まだ存在しない場合（例えば、サンプルデータがシリアライズされる前にメモリ内で構築/操作されている場合）に便利です。

Legolas レコードタイプに関する詳細は https://github.com/beacon-biosignals/Legolas.jl を参照してください。
