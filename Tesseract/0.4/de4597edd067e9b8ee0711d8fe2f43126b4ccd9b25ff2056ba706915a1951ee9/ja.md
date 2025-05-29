```
tess_alto(
    inst::TessInst,
    page::Integer = Int32(1)
)::Union{String, Nothing}
```

画像からALTO形式のテキストを抽出します。エラーが発生した場合は`nothing`を返します。

**引数:**

| T   | 名前   | デフォルト      | 説明                |
|:--- |:---- |:---------- |:----------------- |
| R   | inst |            | テキストを取得するインスタンス。  |
| O   | page | `Int32(1)` | ALTOテキストを抽出するページ。 |

**詳細:**

このメソッドは、画像に対してまだ呼び出されていない場合、`tess_recognize()`を呼び出します。現在のALTO仕様はhttps://github.com/altoxml/documentation/wiki/Versionsでアクセスできます。

**例:**

```jldoctest
using Tesseract

download_languages()

instance = TessInst()
pix = sample_pix()

tess_image(instance, pix)
tess_resolution(instance, 72)

alto = tess_alto(instance)

for line in split(alto, '\n'; keepempty = false)[1:5]
    println(strip(line))
end

# output

<Page WIDTH="500" HEIGHT="600" PHYSICAL_IMG_NR="0" ID="page_0">
<PrintSpace HPOS="0" VPOS="0" WIDTH="500" HEIGHT="600">
<ComposedBlock ID="cblock_0" HPOS="10" VPOS="9" WIDTH="479" HEIGHT="514">
<TextBlock ID="block_0" HPOS="11" VPOS="9" WIDTH="406" HEIGHT="14">
<TextLine ID="line_0" HPOS="11" VPOS="9" WIDTH="406" HEIGHT="14">
```

参照: [`tess_text`](@ref), [`tess_hocr`](@ref), [`tess_tsv`](@ref), [`tess_parsed_tsv`](@ref), [`tess_confidences`](@ref)
