```
map2kmz(mapS::Union{MapS,MapSd,MapS3D},
        map_kmz::String = "map.kmz";
        use_mask::Bool  = true,
        plot_alt::Real  = 0,
        opacity::Real   = 0.75,
        clims::Tuple    = ())
```

Google Earthで使用するための地図のKMZファイルを作成します。 "アイコン"オーバーレイを生成するため、大きな地図（例：> 5度 x 5度）には適していません。

**引数:**

  * `mapS`:     `MapS`、`MapSd`、または`MapS3D`スカラー磁気異常地図構造体
  * `map_kmz`:  （オプション）保存する地図KMZファイルのパス/名前（`.kmz`拡張子はオプション）
  * `use_mask`: （オプション）trueの場合、`mapS`マスクを地図に適用
  * `plot_alt`: （オプション）Google Earthでの地図の高度 [m]
  * `opacity`:  （オプション）地図の不透明度 {0:1}
  * `clims`:    （オプション）長さ`2`の地図カラーバーの制限 `(cmin,cmax)`

**戻り値:**

  * `nothing`: `map_kmz`が作成されます
