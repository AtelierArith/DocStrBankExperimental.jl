```
tess_pipeline_text(
    func::Function,
    pipe::TessPipeline
)::Union{TessOutput, Nothing}
```

パイプラインからテキストファイルを生成し、コールバックを介してクライアントに返します。テキストジェネレーターを出力に追加する際に問題がある場合は`false`を返します。

**引数:**

| T   | 名前   | デフォルト | 説明                  |
|:--- |:---- |:----- |:------------------- |
| R   | func |       | テキストの行で呼び出す関数。      |
| R   | pipe |       | テキストを収集するためのパイプライン。 |

**詳細:**

テキストは呼び出し元に1行ずつ渡されます。行の終端には"\n"が含まれます。

Tesseractはページ間に「ページセパレーター」を挿入します。デフォルトではこの値は"\f"ですが、[`tess_set_param`](@ref)を使用して変更できます。ページを区切るために異なるテキストを使用したい場合は、この関数を呼び出す前に値を設定する必要があります。

**例:**

```jldoctest
using Tesseract

# 読み込むためのページを生成します。
write("page01.tiff", sample_tiff())
write("page02.tiff", sample_tiff())
write("page03.tiff", sample_tiff())

download_languages() # データファイルがあることを確認します。

instance = TessInst()
pipeline = TessPipeline(instance)

count = 0
tess_pipeline_text(pipeline) do line
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

誰も信じなかっただろう、19世紀の最後の年に

この世界が見守られていることを
より大きな知性によって、そして人間と同じように
死すべき存在によって、そして人々が忙しく
自分たちのさまざまな関心事に取り組んでいる間、
彼らは scrutinised and studiedされていた、たぶんほとんど
顕微鏡で一人の人間が一滴の中で群れを成し
増殖する一時的な生物を scrutinise するかのように。

true
```

参照: [`tess_run_pipeline`](@ref), [`tess_pipeline_alto`](@ref),           [`tess_pipeline_hocr`](@ref), [`tess_pipeline_pdf`](@ref)           [`tess_pipeline_tsv`](@ref)
