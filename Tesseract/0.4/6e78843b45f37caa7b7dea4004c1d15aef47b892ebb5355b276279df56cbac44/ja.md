```
tess_pipeline_text(
    pipe::TessPipeline,
    filename::AbstractString
)::Bool
```

パイプラインからテキストファイルを生成し、指定されたファイルに保存します。テキストジェネレーターを出力に追加する際に問題がある場合は `false` を返します。

**引数:**

| T   | 名前       | デフォルト | 説明                  |
|:--- |:-------- |:----- |:------------------- |
| R   | pipe     |       | テキストを収集するためのパイプライン。 |
| R   | filename |       | テキストを書き込むファイル。      |

**詳細:**

ファイルが存在する場合は上書きされます。

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

tess_pipeline_text(pipeline, "My Book.txt")

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
end

for line in readlines("My Book.txt")[1:10]
    println(line)
end

# 出力

No one would have believed in the last years of the

the nineteenth century that this world was being watched
watched keenly and closely by intelligences greater than
than man’s and yet as mortal as his own; that as men busied
busied themselves about their various concerns they were
were scrutinised and studied, perhaps almost as narrowly as
as a man with a microscope might scrutinise the transient
transient creatures that swarm and multiply in a drop of
```

参照: [`tess_run_pipeline`](@ref), [`tess_pipeline_alto`](@ref),           [`tess_pipeline_hocr`](@ref), [`tess_pipeline_pdf`](@ref)           [`tess_pipeline_tsv`](@ref)
