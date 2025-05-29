```
PlotLayoutGeo()
```

---

# 例

---

```
julia>
```

---

# プロパティ

---

  * `bgcolor::String` - 地図の背景色を設定します。タイプ: `color` | デフォルト: `"#fff"`
  * `center::Mcenter` - 詳細についてはMcenterのドキュメントを確認してください。
  * `coastlinecolor::String` - 海岸線の色を設定します。タイプ: `color` | デフォルト: `"#444"`
  * `coastlinewidth::Int` - 海岸線の幅を設定します。タイプ: `number` | デフォルト: `1`
  * `countrywidth::Int` - 国境の線の色を設定します。タイプ: `0`以上の数値 | デフォルト: `1`
  * `fitbounds::Bool` - このサブプロットのビュー設定がトレースデータに合わせて自動計算されるかどうかを決定します。スコープ付き地図では、`fitbounds`を設定すると`center.lon`と`center.lat`が自動的に入力されます。クリップされていない投影の地図では、`fitbounds`を設定すると`center.lon`、`center.lat`、および`projection.rotation.lon`が自動的に入力されます。クリップされた投影の地図では、`fitbounds`を設定すると`center.lon`、`center.lat`、`projection.rotation.lon`、`projection.rotation.lat`、`lonaxis.range`および`lonaxis.range`が自動的に入力されます。 "locations"の場合、トレースの可視位置のみが`fitbounds`計算に考慮されます。 "geojson"の場合、提供されている場合はトレース入力`geojson`全体が`fitbounds`計算に考慮されます。デフォルトは"false"です。タイプ: 列挙型、( false | "locations" | "geojson" )のいずれか
  * `framecolor::String` - フレームの色を設定します。タイプ: `color` | デフォルト: `"#444"`
  * `framewidth::Int` - フレームのストローク幅（px単位）を設定します。タイプ: `0`以上の数値 | デフォルト: `1`
  * `lakecolor::String` - 湖の色を設定します。タイプ: `color` | デフォルト: `"#3399FF"`
  * `landcolor::String` - 陸地の色を設定します。タイプ: `color` | デフォルト: `"#F0DC82"`
  * `lataxis::PlotLayoutAxis` - 詳細についてはPlotLayoutAxisのドキュメントを確認してください。
  * `lonaxis::PlotLayoutAxis` - 詳細についてはPlotLayoutAxisのドキュメントを確認してください。
  * `oceancolor::String` - 海の色を設定します。タイプ: `color` | デフォルト: `"#3399FF"`
  * `geoprojection::GeoProjection` - 詳細についてはGeoProjectionのドキュメントを確認してください。
  * `resolution::String` - 基本レイヤーの解像度を設定します。値はkm/mmの単位を持ち、例えば110はスケール比`1:110,000,000`に対応します。タイプ: 列挙型、( `"110"` | `"50"` )のいずれか | デフォルト: `"110"`
  * `rivercolor::String` - 川の色を設定します。タイプ: `color` | デフォルト: `"#3399FF"`
  * `riverwidth::Int` - 川のストローク幅（px単位）を設定します。タイプ: `0`以上の数値 | デフォルト: `1`
  * `scope::String` - 地図の範囲を設定します。タイプ: 列挙型、( `"world"` | `"usa"` | `"europe"` | `"asia"` | `"africa"` | `"north america"` | `"south america"` )のいずれか | デフォルト: `"world"`
  * `showcoastlines::Bool` - 海岸線を描画するかどうかを設定します。
  * `showcountries::Bool` - 国境を描画するかどうかを設定します。
  * `showframe::Bool` - 地図の周りにフレームを描画するかどうかを設定します。
  * `showlakes::Bool` - 湖を描画するかどうかを設定します。
  * `showland::Bool` - 陸地を色で塗りつぶすかどうかを設定します。
  * `showocean::Bool` - 海を色で塗りつぶすかどうかを設定します。
  * `showrivers::Bool` - 川を描画するかどうかを設定します。
  * `showsubunits::Bool` - 国の中のサブユニット（例: 州、県）の境界を描画するかどうかを設定します。
  * `subunitcolor::String` - サブユニットの境界の色を設定します。タイプ: `color` | デフォルト: `"#444"`
  * `subunitwidth::Int` - サブユニットの境界のストローク幅（px単位）を設定します。タイプ: `0`以上の数値 | デフォルト: `1`
  * `uirevision::Union{String,Int}` - ビュー（投影と中心）におけるユーザー主導の変更の持続性を制御します。デフォルトは`layout.uirevision`です。タイプ: 数値またはカテゴリカル座標文字列
  * `visible::Bool` - 基本レイヤーのデフォルトの可視性を設定します。デフォルト: `true`
