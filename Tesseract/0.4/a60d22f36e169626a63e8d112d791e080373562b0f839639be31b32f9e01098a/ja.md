```
tess_pipeline_alto(
    pipe::TessPipeline,
    filename::AbstractString
)::Bool
```

パイプラインからALTOファイルを生成し、指定されたファイルに保存します。ALTOジェネレーターを出力に追加する際に問題がある場合は`false`を返します。

**引数:**

| T   | 名前       | デフォルト | 説明                      |
|:--- |:-------- |:----- |:----------------------- |
| R   | pipe     |       | ALTOテキストを収集するためのパイプライン。 |
| R   | filename |       | ALTOテキストを書き込むファイル。      |

**詳細:**

ファイルが存在する場合は上書きされます。

**例:**

```jldoctest; filter = r"(\s+)"
using Tesseract

# 読み込むためのページを生成します。
write("page01.tiff", sample_tiff())
write("page02.tiff", sample_tiff())
write("page03.tiff", sample_tiff())

download_languages() # データファイルがあることを確認します。

instance = TessInst()
pipeline = TessPipeline(instance)

tess_pipeline_alto(pipeline, "My Book.xml")

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
end

for line in readlines("My Book.xml")[1:10]
    println(line)
end

# 出力

<?xml version="1.0" encoding="UTF-8"?>
<alto xmlns="http://www.loc.gov/standards/alto/ns-v3#" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.loc.gov/standards/alto/ns-v3# http://www.loc.gov/alto/v3/alto-3-0.xsd">
    <Description>
        <MeasurementUnit>pixel</MeasurementUnit>
        <sourceImageInformation>
            <fileName>My First Book</fileName>
        </sourceImageInformation>
        <OCRProcessing ID="OCR_0">
            <ocrProcessingStep>
                <processingSoftware>
```

関連情報: [`tess_run_pipeline`](@ref), [`tess_pipeline_hocr`](@ref),           [`tess_pipeline_pdf`](@ref), [`tess_pipeline_text`](@ref)           [`tess_pipeline_tsv`](@ref)
