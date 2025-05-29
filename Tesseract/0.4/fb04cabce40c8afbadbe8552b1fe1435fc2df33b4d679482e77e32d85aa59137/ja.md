```
tess_pipeline_pdf(
    pipe::TessPipeline,
    filename::AbstractString;
    textOnly::Bool = false,
    dataDir::AbstractString = TESS_DATA
)::Bool
```

パイプラインからPDFファイルを生成し、指定されたファイルに保存します。PDFジェネレーターを出力に追加する際に問題がある場合は`false`を返します。

**引数:**

| T   | 名前       | デフォルト | 説明                               |
|:--- |:-------- |:----- |:-------------------------------- |
| R   | pipe     |       | tsvを収集するためのパイプライン。               |
| R   | filename |       | tsvを書き込むファイル。                    |
| K   | textOnly |       | PDFにテキストのみを含めるべきか、それとも画像も含めるべきか？ |
| K   | dataDir  |       | PDFフォントファイルを探すディレクトリ。            |

**詳細:**

ファイルが存在する場合は上書きされます。テキストのみのPDFは空に見えますが、Tesseractはグリフなしフォントを使用しているため、テキストを検索することができ、見つかった場所に「空」のページが表示されます。通常、textOnlyはfalseで、Tesseractによってスキャンされた画像を含むため、画像付きの検索可能なPDFが得られます。

**例:**

```jldoctest
using Tesseract

# 読み込むためのページを生成します。
write("page01.tiff", sample_tiff())
write("page02.tiff", sample_tiff())
write("page03.tiff", sample_tiff())

download_languages() # データファイルがあることを確認します。
download_pdf_font() # PDFフォントファイルがあることを確認します。

instance = TessInst()
pipeline = TessPipeline(instance)

tess_pipeline_pdf(pipeline, "My Book.pdf")

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
end

println(string("PDF created: ", filesize("My Book.pdf"), " bytes."))

# 出力

PDF created: 316722 bytes.
```

参照: [`tess_run_pipeline`](@ref), [`tess_pipeline_alto`](@ref),           [`tess_pipeline_hocr`](@ref), [`tess_pipeline_text`](@ref)           [`tess_pipeline_tsv`](@ref)
