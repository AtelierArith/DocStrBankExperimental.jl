```
CachedSVG(svg::SVGDocument)
```

SVGドキュメントと、すでにレンダリングされたCairoサーフェスを持つRsvgハンドルを保持します。

## 使用法

```julia
CachedSVG(read("path/to/svg.svg"))
CachedSVG(read("path/to/svg.svg", String))
CachedSVG(SVGDocument(...))
```

## フィールド

  * `doc`: ここにキャッシュされている元の`SVGDocument`、すなわちそのSVGのテキスト。
  * `handle`: SVGのRsvgハンドルへのポインタ。RsvgによってランダムにGCされる可能性があるため、更新が必要な場合に備えて`Ref`として保存されています。
  * `dims`: アクセスを容易にするためのSVGの寸法（ポイント単位）。
  * `surf`: RsvgがSVGを描画したCairoサーフェス。永続的でキャッシュされています。
  * `image_cache`: （レンダリングされた*画像、スケール*ファクタ）のペアのキャッシュ。これはPDFの再レンダリングを避けるために使用されます。
