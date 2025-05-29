```
plot_map(map_map::Matrix,
         map_xx::Vector       = [],
         map_yy::Vector       = [];
         clims::Tuple         = (),
         dpi::Int             = 200,
         margin::Int          = 2,
         Nmax::Int            = 6*dpi,
         legend::Bool         = true,
         axis::Bool           = true,
         map_color::Symbol    = :usgs,
         bg_color::Symbol     = :white,
         map_units::Symbol    = :rad,
         plot_units::Symbol   = :deg,
         b_e::AbstractBackend = gr())
```

マップをプロットします。

**引数:**

  * `map_map`:    `ny` x `nx` 2D グリッドマップデータ
  * `map_xx`:     `nx` マップ x 方向（経度）座標 [rad] または [deg]
  * `map_yy`:     `ny` マップ y 方向（緯度）座標 [rad] または [deg]
  * `clims`:      （オプション）長さ-`2` カラーバーの制限 `(cmin,cmax)`
  * `dpi`:        （オプション）インチあたりのドット数（画像解像度）
  * `margin`:     （オプション）プロット周囲のマージン [mm]
  * `Nmax`:       （オプション）プロットされるデータポイントの最大数（軸ごと）
  * `legend`:     （オプション）true の場合、凡例を表示
  * `axis`:       （オプション）true の場合、軸を表示
  * `map_color`:  （オプション）塗りつぶし等高線のカラースキーム {`:usgs`,`:gray`,`:gray1`,`:gray2`,`:plasma`,`:magma`}
  * `bg_color`:   （オプション）背景色
  * `map_units`:  （オプション）マップ xx/yy 単位 {`:rad`,`:deg`}
  * `plot_units`: （オプション）プロット xx/yy 単位 {`:rad`,`:deg`,`:m`}
  * `b_e`:        （オプション）プロットバックエンド

**戻り値:**

  * `p1`: マップのプロット
