```
download_pdf_font(;
    target::AbstractString = "tessdata"
    baseUrl::AbstractString = PDF_FONT_URL,
    force::Bool = false
)::Bool
```

PDFフォントファイルをダウンロードします。ファイルのダウンロードに問題がある場合は`false`を返します。

**引数:**

| T   | 名前      | デフォルト      | 説明                       |
|:--- |:------- |:---------- |:------------------------ |
| K   | target  | `tessdata` | PDFフォントを保存するディレクトリ。      |
| K   | baseUrl | ...        | ファイルをダウンロードするためのベースURL。  |
| K   | force   | `false`    | ファイルが存在していてもダウンロードするべきか？ |

**詳細:**

デフォルトでは、"pdf.ttf"はhttps://github.com/tesseract-ocr/tessconfigsからダウンロードされます。クライアントは、ファイルをダウンロードするための異なるURLを指定できます。このファイルは、TesseractにPDFを生成するように依頼する際に必要です。

通常、ファイルがすでにダウンロードされている場合は再度ダウンロードされません。ただし、`force`がtrueの場合は、ファイルがダウンロードされ、既存のファイルが上書きされます。

関連情報: [`update_pdf_font`](@ref)
