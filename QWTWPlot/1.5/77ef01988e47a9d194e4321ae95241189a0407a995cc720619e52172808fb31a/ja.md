```
qmglmesh(data::Array{Float64, 2}, xMin = -10.0, xMax = 10.0, yMin = -10.0, yMax = 10.0,  style::String = ""; name = "", type = 0)
```

3Dメッシュ/サーフェスを描画します。 現在、Linuxのみで動作します（これは本当ですか？）。   data - サーフェスの垂直（z）座標。 Array{Float64, 2}である必要があります。 xMin, xMax, yMin, yMaxは、サーフェスを描画する範囲の定義です。 'data'のすべての座標は、この範囲内に均等に分布しています。 style サーフェスの描画方法。 いくつかのヒントはここから得られます: http://mathgl.sourceforge.net/doc_en/Color-scheme.html  type  -   0または1; メッシュ/グリッドまたはサーフェス name - まだ使用されていません（後で追加するかもしれません）
