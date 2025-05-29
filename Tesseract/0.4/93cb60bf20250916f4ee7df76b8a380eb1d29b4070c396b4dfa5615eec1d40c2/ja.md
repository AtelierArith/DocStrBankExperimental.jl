```
tess_pipeline_text(
    pipe::TessPipeline
)::Union{TessOutput{String}, Nothing}
```

パイプラインからテキストファイルを生成し、文字列に保存します。テキストジェネレーターを出力に追加する際に問題がある場合は `nothing` を返します。

**引数:**

| T   | 名前   | デフォルト | 説明                  |
|:--- |:---- |:----- |:------------------- |
| R   | pipe |       | テキストを収集するためのパイプライン。 |

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

book = tess_pipeline_text(pipeline)

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
end

count = 0
for line in split(book[], "\n")[1:10]
    global count
    if count < 10
        println(line)
    end
    count += 1
end

# 出力

誰も最後の年に信じることはなかった

19世紀のこの世界が見守られていることを
より大きな知性によって注意深く見守られていることを
人間のそれと同じように死すべきものであることを; 男たちが
さまざまな関心事に忙しくしている間、彼らは
注意深く観察され、研究されていた、たぶんほとんど
顕微鏡で一人の男が一滴の中で群れを成し
増殖する一時的な生物を観察するかのように。
```

関連情報: [`tess_run_pipeline`](@ref), [`tess_pipeline_alto`](@ref),           [`tess_pipeline_hocr`](@ref), [`tess_pipeline_pdf`](@ref)           [`tess_pipeline_tsv`](@ref)
