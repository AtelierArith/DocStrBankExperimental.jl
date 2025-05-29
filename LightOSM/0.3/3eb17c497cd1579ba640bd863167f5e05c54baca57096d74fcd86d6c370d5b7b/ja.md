```
buildings_from_file(file_path::String)::Dict{Integer,Building}
```

OpenStreetMapデータファイル（`:osm`、`:xml`、または`:json`形式）から`Building`オブジェクトを作成します。

# 引数

  * `file_path::String`: OpenStreetMapデータファイルへのパス。

# 戻り値

  * `Dict{Integer,Building}`: 建物のリレーション/ウェイIDから`Building`オブジェクトへのマッピング。
