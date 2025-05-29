```
tess_pipeline_word_box(
    func::Function,
    pipe::TessPipeline
)::Bool
```

パイプラインからBOXファイルを生成し、コールバックを介してクライアントに返します。BOXジェネレーターを出力に追加する際に問題がある場合は`false`を返します。

**引数:**

| T   | 名前   | デフォルト | 説明                    |
|:--- |:---- |:----- |:--------------------- |
| R   | func |       | テキストの行で呼び出す関数。        |
| R   | pipe |       | BOXデータを収集するためのパイプライン。 |

**詳細:**

テキストは呼び出し元に1行ずつ渡されます。行終端子の"\n"はテキストに含まれます。

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
tess_pipeline_word_box(pipeline) do line
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

WordStr 11 577 417 591 0 #誰もが信じなかった、最後の数年間の
   418 577 422 591 0
WordStr 11 557 457 571 0 #19世紀のこの世界が見守られていることを
   458 557 462 571 0
WordStr 10 537 457 551 0 #より大きな知性によって注意深く見守られていることを
   458 537 462 551 0
WordStr 11 517 481 531 0 #人間のものよりも、そして彼自身と同じように死すべきものであることを; 男たちが
   482 517 486 531 0
WordStr 11 497 457 511 0 #さまざまな関心事に忙しくしている間に
   458 497 462 511 0
true
```

参照: [`tess_run_pipeline`](@ref), [`tess_pipeline_unlv`](@ref),           [`tess_pipeline_lstm_box`](@ref)
