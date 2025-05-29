```
map_gxf2h5(map_gxf::String, alt::Real;
           map_info::String = splitpath(map_gxf)[end],
           fill_map::Bool   = true,
           get_lla::Bool    = true,
           zone_utm::Int    = 18,
           is_north::Bool   = true,
           save_h5::Bool    = false,
           map_h5::String   = "map_data.h5")
```

GXFからHDF5へのマップデータファイルを変換します（`UTM`グリッドを仮定）。操作の順序は次のとおりです：

  * `map_gxf`からの元のマップ =>
  * マップデータが欠落している大きな領域をトリミング =>
  * 残りのマップデータが欠落している領域を埋める =>
  * マップグリッドを`UTM`から`LLA`に変換

特にSMALLおよびLEVELマップ専用です。

**引数:**

  * `map_gxf`:  対象（例：磁気）マップGXFファイルのパス/名前（`.gxf`拡張子はオプション）
  * `alt`:      マップの高度 [m]
  * `map_info`: （オプション）マップ情報
  * `fill_map`: （オプション）trueの場合、マップデータが欠落している領域を埋める
  * `get_lla`:  （オプション）trueの場合、マップグリッドを`UTM`から`LLA`に変換
  * `zone_utm`: （オプション）UTMゾーン
  * `is_north`: （オプション）trueの場合、マップは北半球にある
  * `save_h5`:  （オプション）trueの場合、`mapS`を`map_h5`に保存
  * `map_h5`:   （オプション）保存するマップデータHDF5ファイルのパス/名前（`.h5`拡張子はオプション）

**戻り値:**

  * `mapS`: `MapS`スカラー磁気異常マップ構造体
