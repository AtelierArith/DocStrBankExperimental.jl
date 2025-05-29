```
tess_pipeline_unlv_latin1(
    pipe::TessPipeline
)::Union{TessOutput{Vector{UInt8}}, Nothing}
```

パイプラインからUNLVファイルを生成し、バイト配列に保存します。 UNLVジェネレーターを出力に追加する際に問題がある場合は、`nothing`を返します。

**引数:**

| T   | 名前   | デフォルト | 説明                      |
|:--- |:---- |:----- |:----------------------- |
| R   | pipe |       | UNLVテキストを収集するためのパイプライン。 |

**詳細:**

返されるバイトはLatin-1エンコーディングであるため、Juliaで文字列として使用する前に変換が必要です。 [`tess_pipeline_unlv`](@ref)は、すでにUTF-8でエンコードされた同じデータを提供します。

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

bytes = tess_pipeline_unlv_latin1(pipeline)

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
end

println(string("生成された本: ", length(bytes[]), " バイト。"))

# 出力

生成された本: 4410 バイト。
```

参照: [`tess_run_pipeline`](@ref), [`tess_pipeline_word_box`](@ref),           [`tess_pipeline_lstm_box`](@ref), [`tess_pipeline_unlv`](@ref)
