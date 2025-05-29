```
get_google_route(origin::Int, destination::Int,
                 map_data:MapData, googleapi_key::String;
                 googleapi_parameters::Dict{Symbol,String} = googleAPI_parameters)
```

Google Distances APIを使用して、地図`map_data`上の2つのポイント（`origin`と`destination`）に基づいてルートを取得します。Google APIキー`googleapi_key`とオプションのGoogle Distances APIリクエストパラメータ`googleapi_parameters`を使用します。
