```
buildings_from_object(buildings_json_object::AbstractDict)::Dict{Integer,Building}
```

`download_osm_buildings` でダウンロードしたデータから `Building` オブジェクトを作成します。

# 引数

  * `buildings_json_object::AbstractDict`: `:json` 形式でダウンロードした建物データ。

# 返り値

  * `Dict{Integer,Building}`: 建物のリレーション/ウェイIDから `Building` オブジェクトへのマッピング。
