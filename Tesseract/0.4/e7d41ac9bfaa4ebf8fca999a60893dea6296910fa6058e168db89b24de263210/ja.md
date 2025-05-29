```
tess_pipeline_lstm_box(
    func::Function,
    pipe::TessPipeline
)::Bool
```

パイプラインからLSTM BOXファイルを生成し、コールバックを介してクライアントに返します。LSTM BOXジェネレーターを出力に追加する際に問題がある場合は`false`を返します。

**引数:**

| T   | 名前   | デフォルト | 説明                         |
|:--- |:---- |:----- |:-------------------------- |
| R   | func |       | テキストの行で呼び出す関数。             |
| R   | pipe |       | LSTM BOXデータを収集するためのパイプライン。 |

**詳細:**

テキストは呼び出し元に1行ずつ渡されます。行終端子の"\n"はテキストに含まれます。

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
tess_pipeline_lstm_box(pipeline) do line
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
true
```

参照: [`tess_run_pipeline`](@ref), [`tess_pipeline_word_box`](@ref),           [`tess_pipeline_unlv`](@ref)
