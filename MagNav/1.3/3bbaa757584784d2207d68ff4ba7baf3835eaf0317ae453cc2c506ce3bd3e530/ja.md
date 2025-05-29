```
map_gxf2h5(map_gxf::String, alt_gxf::String, alt::Real;
           map_info::String    = splitpath(map_gxf)[end],
           pad::Int            = 0,
           sub_igrf_date::Real = get_years(2013,293),
           add_igrf_date::Real = -1,
           zone_utm::Int       = 18,
           is_north::Bool      = true,
           fill_map::Bool      = true,
           up_cont::Bool       = true,
           down_cont::Bool     = true,
           get_lla::Bool       = true,
           dz::Real            = 5,
           down_max::Real      = 150,
           α::Real             = 200,
           save_h5::Bool       = false,
           map_h5::String      = "map_data.h5")
```

GXFからHDF5へのマップデータファイルを変換します（`UTM`グリッドを仮定）。操作の順序は次のとおりです：

  * `map_gxf`からの元のマップ =>
  * マップデータが欠落している大きな領域をトリミング =>
  * マップデータにIGRFを加算および/または減算 =>
  * マップデータが欠落している残りの領域を埋める =>
  * `alt`に向けて上方/下方に続ける =>
  * マップグリッドを`UTM`から`LLA`に変換

これはメモリを多く消費する可能性があり、主にマップのサイズと`dz`に依存します。`up_cont = true`の場合、`MapS`構造体が返されます。`up_cont = false`の場合、標高マップが含まれる`MapSd`構造体が返されます。

**引数:**

  * `map_gxf`:       対象（例：磁気）マップGXFファイルのパス/名前（`.gxf`拡張子はオプション）
  * `alt_gxf`:       標高マップGXFファイルのパス/名前（`.gxf`拡張子はオプション）
  * `alt`:           上方継続後の最終マップ標高 [m]、ドレープマップには使用されません
  * `map_info`:      （オプション）マップ情報
  * `pad`:           （オプション）マップの端に沿った最小パディング（グリッドセル）
  * `sub_igrf_date`: （オプション）減算するIGRFコアフィールドの日付 [年]、無視するには-1
  * `add_igrf_date`: （オプション）加算するIGRFコアフィールドの日付 [年]、無視するには-1
  * `zone_utm`:      （オプション）UTMゾーン
  * `is_north`:      （オプション）trueの場合、マップは北半球にあります
  * `fill_map`:      （オプション）trueの場合、マップデータが欠落している領域を埋めます
  * `up_cont`:       （オプション）trueの場合、`alt`に向けて上方/下方に続けます
  * `down_cont`:     （オプション）trueの場合、必要に応じて下方に続けます。`up_cont = true`の場合のみ使用されます
  * `get_lla`:       （オプション）trueの場合、マップグリッドを`UTM`から`LLA`に変換します
  * `dz`:            （オプション）上方継続のステップサイズ [m]
  * `down_max`:      （オプション）最大下方継続距離 [m]
  * `α`:             （オプション）下方継続の正則化パラメータ
  * `save_h5`:       （オプション）trueの場合、`mapS`を`map_h5`に保存します
  * `map_h5`:        （オプション）保存するマップデータHDF5ファイルのパス/名前（`.h5`拡張子はオプション）

**戻り値:**

  * `mapS`: `MapS`または`MapSd`スカラー磁気異常マップ構造体
