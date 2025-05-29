```
path2kml(lat::Vector, lon::Vector, alt::Vector,
         path_kml::String   = "path.kml";
         path_units::Symbol = :rad,
         width::Int         = 3,
         color1::String     = "ff000000",
         color2::String     = "80000000",
         points::Bool       = false)
```

Google Earthで使用するための飛行経路のKMLファイルを作成します。

**引数:**

  * `lat`:        緯度  [rad] または [deg]
  * `lon`:        経度 [rad] または [deg]
  * `alt`:        高度  [m]
  * `path_kml`:   (オプション) 保存する飛行経路KMLファイルのパス/名前（`.kml`拡張子はオプション）
  * `path_units`: (オプション) `lat`/`lon`の単位 {`:rad`,`:deg`}
  * `width`:      (オプション) 線の幅
  * `color1`:     (オプション) 経路の色
  * `color2`:     (オプション) 経路の下の色
  * `points`:     (オプション) trueの場合、線の代わりに点を作成

**戻り値:**

  * `nothing`: `path_kml`が作成されます
