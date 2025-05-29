```
tess_pipeline_lstm_box(
    pipe::TessPipeline
)::Union{TessOutput{String}, Nothing}
```

パイプラインからLSTM BOXファイルを生成し、文字列に保存します。LSTM BOXジェネレーターを出力に追加する際に問題が発生した場合は`nothing`を返します。

**引数:**

| T   | 名前   | デフォルト | 説明                         |
|:--- |:---- |:----- |:-------------------------- |
| R   | pipe |       | LSTM BOXデータを収集するためのパイプライン。 |

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

book = tess_pipeline_lstm_box(pipeline)

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
end

for line in split(book[], "\n")[1:10]
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
