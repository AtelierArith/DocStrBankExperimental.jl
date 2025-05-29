```
tess_text(
    inst::TessInst
)::Union{String, Nothing}
```

画像からテキストを抽出します。エラーが発生した場合は `nothing` が返されます。

**引数:**

| T   | 名前   | デフォルト | 説明               |
|:--- |:---- |:----- |:---------------- |
| R   | inst |       | テキストを取得するインスタンス。 |

**詳細:**

このメソッドは、画像に対してまだ `tess_recognize()` が呼び出されていない場合に呼び出されます。

**例:**

```jldoctest
using Tesseract

download_languages()

instance = TessInst()
pix = sample_pix()

tess_image(instance, pix)
tess_resolution(instance, 72)

text = tess_text(instance)

for line in split(text, '\n'; keepempty = false)[1:5]
    println(line)
end

# 出力

No one would have believed in the last years of the
the nineteenth century that this world was being watched
watched keenly and closely by intelligences greater than
than man’s and yet as mortal as his own; that as men busied
busied themselves about their various concerns they were
```

参照: [`tess_hocr`](@ref), [`tess_alto`](@ref), [`tess_tsv`](@ref),           [`tess_parsed_tsv`](@ref), [`tess_confidences`](@ref)
