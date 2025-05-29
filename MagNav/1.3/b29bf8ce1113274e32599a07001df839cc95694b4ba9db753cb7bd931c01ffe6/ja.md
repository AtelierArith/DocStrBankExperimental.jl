```
map2kmz(map_map::Matrix, map_xx::Vector, map_yy::Vector,
        map_kmz::String   = "map.kmz";
        map_units::Symbol = :rad,
        plot_alt::Real    = 0,
        opacity::Real     = 0.75,
        clims::Tuple      = ())
```

Google Earthで使用するための地図のKMZファイルを作成します。 "アイコン"オーバーレイを生成するため、大きな地図（例：> 5度 x 5度）には適していません。

**引数:**

  * `map_map`:   `ny` x `nx` 2Dグリッドマップデータ
  * `map_xx`:    `nx` マップのx方向（経度）座標 [rad] または [deg]
  * `map_yy`:    `ny` マップのy方向（緯度）座標 [rad] または [deg]
  * `map_kmz`:   （オプション）保存するマップKMZファイルのパス/名前（`.kmz`拡張子はオプション）
  * `map_units`: （オプション）マップxx/yy単位 {`:rad`,`:deg`}
  * `plot_alt`:  （オプション）Google Earthでのマップの高度 [m]
  * `opacity`:   （オプション）マップの不透明度 {0:1}
  * `clims`:     （オプション）長さ`2`のマップカラーバーの制限 `(cmin,cmax)`

**戻り値:**

  * `nothing`: `map_kmz`が作成されます
