```
get_google_route(origin::Int, destination::Int, waypoint::Int,
                 map_data:MapData, googleapi_key::String;
                 googleapi_parameters::Dict{Symbol,String} = googleAPI_parameters)
```

Google Distances APIを使用して、地図`map_data`上の3つのポイント（`origin`、`destination`、およびその間の`waypoint`）に基づいてルートを取得します。Google APIキー`googleapi_key`を使用し、オプションのGoogle Distances APIリクエストパラメータ`googleapi_parameters`を指定できます。
