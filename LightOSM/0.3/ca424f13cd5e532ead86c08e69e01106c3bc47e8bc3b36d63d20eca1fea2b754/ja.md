```
buildings_from_object(buildings_xml_object::XMLDocument)::Dict{Integer,Building}
```

`download_osm_buildings`でダウンロードしたデータから`Building`オブジェクトを作成します。

# 引数

  * `buildings_xml_object::XMLDocument`: `:xml`または`:osm`形式でダウンロードされた建物データ。

# 戻り値

  * `Dict{Integer,Building}`: 建物のリレーション/ウェイIDから`Building`オブジェクトへのマッピング。
