```
load_map_from_json!(m::KeplerGLMap, json_map_file::String)
```

`json_map_file`から地図`m`にkepler.glマップファイルを読み込みます。既存のマップ設定とデータセットは上書きされます。

# 必要な引数

  * `m::KeplerGLMap`: 設定とデータを適用するマップ。
  * `json_map_file::String`: kepler.gl JSONマップファイルへのパス。
