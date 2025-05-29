```
tess_pipeline_hocr(
    func::Function,
    pipe::TessPipeline,
    fontInfo::Bool = false
)::Bool
```

パイプラインからHOCRファイルを生成し、コールバックを介してクライアントに返します。出力にHOCRジェネレーターを追加する際に問題がある場合は`false`を返します。

**引数:**

| T   | 名前       | デフォルト   | 説明                  |
|:--- |:-------- |:------- |:------------------- |
| R   | func     |         | テキストの行で呼び出す関数。      |
| R   | pipe     |         | テキストを収集するためのパイプライン。 |
| O   | fontInfo | `false` | 出力にフォント情報を含めるべきか？   |

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
tess_pipeline_hocr(pipeline) do line
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
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
    <head>
        <title>My First Book</title>
        <meta http-equiv="Content-Type" content="text/html;charset=utf-8"/>
        <meta name='ocr-system' content='tesseract 5.1.0' />
        <meta name='ocr-capabilities' content='ocr_page ocr_carea ocr_par ocr_line ocrx_word ocrp_wconf'/>
    </head>
true
```

参照: [`tess_run_pipeline`](@ref), [`tess_pipeline_alto`](@ref),           [`tess_pipeline_pdf`](@ref), [`tess_pipeline_text`](@ref)           [`tess_pipeline_tsv`](@ref)
