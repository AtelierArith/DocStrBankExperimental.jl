```
tess_pipeline_tsv(
    pipe::TessPipeline
)::Union{TessOutput{String}, Nothing}
```

パイプラインからTSVファイルを生成し、文字列に保存します。TSVジェネレーターを出力に追加する際に問題がある場合は`nothing`を返します。

**引数:**

| T   | 名前   | デフォルト | 説明                    |
|:--- |:---- |:----- |:--------------------- |
| R   | pipe |       | TSVデータを収集するためのパイプライン。 |

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

book = tess_pipeline_tsv(pipeline)

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
    true
end

for line in split(book[], "\n")[1:10]
    println(line)
end

# 出力

level	page_num	block_num	par_num	line_num	word_num	left	top	width	height	conf	text
1	1	0	0	0	0	0	0	500	600	-1
2	1	1	0	0	0	10	9	479	514	-1
3	1	1	1	0	0	11	9	406	14	-1
4	1	1	1	1	0	11	9	406	14	-1
5	1	1	1	1	1	11	9	14	11	95.791931	No
5	1	1	1	1	2	35	12	22	8	95.791931	one
5	1	1	1	1	3	66	9	39	11	92.953789	would
5	1	1	1	1	4	115	9	30	11	92.953789	have
5	1	1	1	1	5	155	9	62	11	96.819153	believed
```

関連情報: [`tess_run_pipeline`](@ref), [`tess_pipeline_alto`](@ref),           [`tess_pipeline_hocr`](@ref), [`tess_pipeline_pdf`](@ref)           [`tess_pipeline_text`](@ref)
