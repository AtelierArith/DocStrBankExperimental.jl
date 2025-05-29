```
CachedPDF(pdf::PDFDocument)
```

PDFドキュメントと、すでにレンダリングされたCairoサーフェスを持つPopplerハンドルを保持します。

## 使用法

```julia
CachedPDF(read("path/to/pdf.pdf"), [page = 0])
CachedPDF(read("path/to/pdf.pdf", String), [page = 0])
CachedPDF(PDFDocument(...), [page = 0])
```

## フィールド

  * `doc`: ここにキャッシュされている`PDFDocument`への参照。
  * `ptr`: PDFのPopplerハンドルへのポインタ。PopplerによってランダムにGCされる可能性があります。
  * `dims`: アクセスを容易にするためのPDFページの寸法（ポイント単位）。
  * `surf`: PopplerがPDFを描画したCairoサーフェス。永続的でキャッシュされています。
  * `image_cache`: （レンダリングされた*画像、スケール*ファクター）ペアのキャッシュ。PDFの再レンダリングを避けるために使用されます。
