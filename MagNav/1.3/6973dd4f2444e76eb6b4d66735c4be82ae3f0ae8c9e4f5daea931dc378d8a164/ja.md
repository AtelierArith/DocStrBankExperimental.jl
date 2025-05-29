```
plot_map!(p1::Plot, mapS::Union{MapS,MapSd,MapS3D};
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
          plot_units::Symbol   = :deg
          b_e::AbstractBackend = gr())
```

既存のプロットに地図をプロットします。

**引数:**

  * `p1`:         プロット
  * `mapS`:       `MapS`、`MapSd`、または `MapS3D` スカラー磁気異常マップ構造体
  * `use_mask`:   （オプション）true の場合、`mapS` マスクを地図に適用
  * `clims`:      （オプション）長さ `2` のカラーバー制限 `(cmin,cmax)`
  * `dpi`:        （オプション）インチあたりのドット数（画像解像度）
  * `margin`:     （オプション）プロット周囲のマージン [mm]
  * `Nmax`:       （オプション）プロットされるデータポイントの最大数（軸ごと）
  * `legend`:     （オプション）true の場合、凡例を表示
  * `axis`:       （オプション）true の場合、軸を表示
  * `map_color`:  （オプション）塗りつぶし等高線のカラースキーム {`:usgs`,`:gray`,`:gray1`,`:gray2`,`:plasma`,`:magma`}
  * `bg_color`:   （オプション）背景色
  * `map_units`:  （オプション）地図の xx/yy 単位 {`:rad`,`:deg`}
  * `plot_units`: （オプション）プロットの xx/yy 単位 {`:rad`,`:deg`,`:m`}
  * `b_e`:        （オプション）プロットバックエンド

**戻り値:**

  * `nothing`: `p1` に地図がプロットされます
