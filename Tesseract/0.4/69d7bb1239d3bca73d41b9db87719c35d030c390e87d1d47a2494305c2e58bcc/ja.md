```
tess_pipeline_word_box(
    pipe::TessPipeline,
    filename::AbstractString
)::Bool
```

パイプラインからBOXファイルを生成し、指定されたファイルに保存します。BOXジェネレーターを出力に追加する際に問題がある場合は`false`を返します。

**引数:**

| T   | 名前       | デフォルト | 説明                 |
|:--- |:-------- |:----- |:------------------ |
| R   | pipe     |       | BOXを収集するためのパイプライン。 |
| R   | filename |       | BOXを書き込むファイル。      |

**詳細:**

ファイルが存在する場合は上書きされます。

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

tess_pipeline_word_box(pipeline, "My Book.box")

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
end

for line in readlines("My Book.box")[1:10]
    println(line)
end

# 出力

WordStr 11 577 417 591 0 #誰もが信じなかった、最後の数年間の
   418 577 422 591 0
WordStr 11 557 457 571 0 #19世紀のこの世界が見守られていることを
   458 557 462 571 0
WordStr 10 537 457 551 0 #より大きな知性によって注意深く見守られていることを
   458 537 462 551 0
WordStr 11 517 481 531 0 #人間のものよりも、そして彼自身と同じように死すべきものであることを；人々が
   482 517 486 531 0
WordStr 11 497 457 511 0 #さまざまな関心事に忙しくしている間、彼らは
   458 497 462 511 0
```

参照: [`tess_run_pipeline`](@ref), [`tess_pipeline_unlv`](@ref),           [`tess_pipeline_lstm_box`](@ref)
