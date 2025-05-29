```
Geocoder(cities_data::AbstractDataFrame; filters::Vector{Function} = Function[])
Geocoder(;
    data_dir::String=DATA_DIR, 
    geo_file::String=GEO_FILE, 
    decoder_output_columns::Vector{Symbol} = DEFAULT_DECODER_OUTPUT,
    filters::Vector{Function} = Function[]
)
```

参照点とそのラベル（都市名と国コード）を保持するGeocoder構造体。

2番目のコンストラクタは、最初の実行時に自動的にダウンロードされる地名データからGeocoderを作成するために使用されます。
