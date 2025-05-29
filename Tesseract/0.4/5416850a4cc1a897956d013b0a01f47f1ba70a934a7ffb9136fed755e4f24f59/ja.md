```
tess_pipeline_unlv(
    pipe::TessPipeline
)::Union{TessOutput{String}, Nothing}
```

パイプラインからUNLVファイルを生成し、文字列に保存します。UNLVジェネレーターを出力に追加する際に問題がある場合は`nothing`を返します。

**引数:**

| T   | 名前   | デフォルト | 説明                      |
|:--- |:---- |:----- |:----------------------- |
| R   | pipe |       | UNLVテキストを収集するためのパイプライン。 |

**詳細:**

TesseractはLatin-1テキストを生成しますが、この関数はそれをUTF-8にトランスコードしてJuliaと正しく相互作用します。

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

book = tess_pipeline_unlv(pipeline)

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
end

for line in split(book[], "\n")[1:10]
    println(line)
end

# 出力

誰も19世紀の最後の年に、この世界が
人間よりも優れた知性によって
注意深く見守られているとは信じなかった。
人々がさまざまな関心事に忙しくしている間、
彼らは scrutinised and studiedされていた。
おそらく顕微鏡で一人の男が
水滴の中に群がり増殖する
一時的な生物を scrutiniseするのと同じくらい狭く。
無限の自己満足で人々はこの地球を行き来し、
彼らの小さな事務において安らかであった。
```

関連情報: [`tess_run_pipeline`](@ref), [`tess_pipeline_word_box`](@ref),           [`tess_pipeline_lstm_box`](@ref), [`tess_pipeline_unlv_latin1`](@ref)
