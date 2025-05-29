```
プロバイダー

プロバイダー(url; name=nothing, max_zoom=18, attribution="")
```

`OSM`、`Esri`などのベースレイヤータイルプロバイダーのパラメーターを定義します。

`Provider`は、カスタムタイルプロバイダーのために手動で定義することもできます。

# 引数

  * `url`: URLタイルパス、例: "http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"

# キーワード

  * `name`: プロバイダーのための`Symbol`名、または`nothing`

# 例

OpenStreetMapプロバイダーを手動で定義します。

```julia
using Blink, Leaflet

```

julia url = "http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png" provider = Leaflet.Provider(url)

w = Blink.Window() body!(w, Leaflet.Map(; provider, zoom=3, height=1000))
