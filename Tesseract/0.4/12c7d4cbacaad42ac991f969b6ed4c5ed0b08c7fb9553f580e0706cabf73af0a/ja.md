```
tess_pipeline_unlv(
    pipe::TessPipeline,
    filename::AbstractString,
    utf8::Bool = true
)::Bool
```

パイプラインからUNLVテストファイルを生成し、指定されたファイルに保存します。 UNLVジェネレーターを出力に追加する際に問題がある場合は`false`を返します。

**引数:**

| T   | 名前       | デフォルト  | 説明                      |
|:--- |:-------- |:------ |:----------------------- |
| R   | pipe     |        | UNLVテキストを収集するためのパイプライン。 |
| R   | filename |        | UNLVテキストを書き込むファイル。      |
| O   | utf8     | `true` | 出力をUTF-8に変換するべきか？       |

**詳細:**

ファイルが存在する場合は上書きされます。 Tesseractライブラリは、すべての他の形式がUTF-8であるにもかかわらず、Latin-1エンコーディングでファイルを出力します。 必要に応じて、Juliaを使用してファイルをUTF-8に変換し、他のエンコーディングと一致させることができます。

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

tess_pipeline_unlv(pipeline, "My Book.unlv")

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
end

for line in readlines("My Book.unlv")[1:10]
    println(line)
end

# 出力

No one would have believed in the last years of the
the nineteenth century that this world was being watched
watched keenly and closely by intelligences greater than
than man's and yet as mortal as his own; that as men busied
busied themselves about their various concerns they were
were scrutinised and studied, perhaps almost as narrowly as
as a man with a microscope might scrutinise the transient
transient creatures that swarm and multiply in a drop of
of water. With infinite complacency men went to and fro over
over this globe about their little affairs, serene in their
```

参照: [`tess_run_pipeline`](@ref), [`tess_pipeline_word_box`](@ref),           [`tess_pipeline_lstm_box`](@ref), [`tess_pipeline_unlv_latin1`](@ref)
