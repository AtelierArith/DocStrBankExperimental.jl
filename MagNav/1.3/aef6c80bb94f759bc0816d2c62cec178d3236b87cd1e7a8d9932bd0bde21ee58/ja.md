```
plot_map(map_map::Map;
         use_mask::Bool       = true,
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

  * `map_map`:    `Map` 磁気異常マップ構造体
  * `use_mask`:   （オプション）trueの場合、`map_map` マスクをマップに適用
  * `clims`:      （オプション）長さ`2`のカラーバー制限 `(cmin,cmax)`
  * `dpi`:        （オプション）ドット毎インチ（画像解像度）
  * `margin`:     （オプション）プロット周囲のマージン [mm]
  * `Nmax`:       （オプション）プロットされるデータポイントの最大数（軸ごと）
  * `legend`:     （オプション）trueの場合、凡例を表示
  * `axis`:       （オプション）trueの場合、軸を表示
  * `map_color`:  （オプション）塗りつぶし等高線のカラースキーム {`:usgs`,`:gray`,`:gray1`,`:gray2`,`:plasma`,`:magma`}
  * `bg_color`:   （オプション）背景色
  * `map_units`:  （オプション）マップの xx/yy 単位 {`:rad`,`:deg`}
  * `plot_units`: （オプション）プロットの xx/yy 単位 {`:rad`,`:deg`,`:m`}
  * `b_e`:        （オプション）プロットバックエンド

**戻り値:**

  * `p1`: マップのプロット（`map_map isa MapV`の場合、`mapX`）
  * `p2`: `map_map isa MapV`の場合、`mapY`
  * `p3`: `map_map isa MapV`の場合、`mapZ`
