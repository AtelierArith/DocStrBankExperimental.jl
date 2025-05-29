```
tess_pipeline_alto(
    func::Function,
    pipe::TessPipeline
)::Bool
```

パイプラインからALTOファイルを生成し、コールバックを介してクライアントに返します。ALTOジェネレーターを出力に追加する際に問題がある場合は`false`を返します。

**引数:**

| T   | 名前   | デフォルト | 説明                  |
|:--- |:---- |:----- |:------------------- |
| R   | func |       | テキストの行で呼び出す関数。      |
| R   | pipe |       | テキストを収集するためのパイプライン。 |

**詳細:**

テキストは呼び出し元に1行ずつ渡されます。テキストには"\n"行終端子が含まれます。

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

count = 0
tess_pipeline_alto(pipeline) do line
    global count
    if count < 10
        print(line)
    end
    count += 1
end

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
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
true
```

参照: [`tess_run_pipeline`](@ref), [`tess_pipeline_hocr`](@ref),           [`tess_pipeline_pdf`](@ref), [`tess_pipeline_text`](@ref)           [`tess_pipeline_tsv`](@ref)
