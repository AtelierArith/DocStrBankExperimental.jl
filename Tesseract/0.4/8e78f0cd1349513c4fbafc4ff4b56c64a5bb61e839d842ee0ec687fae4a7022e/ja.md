```
tess_pipeline_lstm_box(
    pipe::TessPipeline,
    filename::AbstractString
)::Bool
```

パイプラインからLSTM BOXファイルを生成し、指定されたファイルに保存します。LSTM BOXジェネレーターを出力に追加する際に問題がある場合は`false`を返します。

**引数:**

| T   | 名前       | デフォルト | 説明                      |
|:--- |:-------- |:----- |:----------------------- |
| R   | pipe     |       | LSTM BOXを収集するためのパイプライン。 |
| R   | filename |       | LSTM BOXを書き込むファイル。      |

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

tess_pipeline_lstm_box(pipeline, "My Book.box")

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
    true
end

for line in readlines("My Book.box")[1:10]
    println(line)
end

# 出力

N 11 577 422 591 0
o 11 577 422 591 0
  11 577 422 591 0
o 11 577 422 591 0
n 11 577 422 591 0
e 11 577 422 591 0
  11 577 422 591 0
w 11 577 422 591 0
o 11 577 422 591 0
u 11 577 422 591 0
```

参照: [`tess_run_pipeline`](@ref), [`tess_pipeline_word_box`](@ref),           [`tess_pipeline_unlv`](@ref)
