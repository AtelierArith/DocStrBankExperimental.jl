```
tess_pipeline_unlv(
    func::Function,
    pipe::TessPipeline
)::Bool
```

パイプラインからUNLVファイルを生成し、コールバックを介してクライアントに返します。UNLVジェネレーターを出力に追加する際に問題がある場合は`false`を返します。

**引数:**

| T   | 名前   | デフォルト | 説明                  |
|:--- |:---- |:----- |:------------------- |
| R   | func |       | テキストの行で呼び出す関数。      |
| R   | pipe |       | テキストを収集するためのパイプライン。 |

**詳細:**

テキストは呼び出し元に1行ずつ渡されます。テキストには"\n"行終端子が含まれます。TesseractはUNLVテキストをLatin-1で生成しますが、このメソッドはそれをUTF-8にトランスコードしてJuliaで使用できるようにします。

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
tess_pipeline_unlv(pipeline) do line
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

誰も19世紀の最後の年に、この世界が
人間よりも大きな知性によって
注意深く見守られているとは信じなかった。
人々がさまざまな関心事に忙しくしている間、
彼らはおそらく顕微鏡で
一滴の水の中に群がり増殖する
一時的な生物を scrutinise するかのように
精査され、研究されていた。無限の自己満足で
人々はこの地球を行き来し、
彼らの小さな事務に没頭していた。
```

他にも参照: [`tess_run_pipeline`](@ref), [`tess_pipeline_word_box`](@ref),           [`tess_pipeline_lstm_box`](@ref), [`tess_pipeline_unlv_latin1`](@ref)
