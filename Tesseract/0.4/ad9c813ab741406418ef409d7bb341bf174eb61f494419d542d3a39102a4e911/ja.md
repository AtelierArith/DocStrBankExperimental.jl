```
tess_confidences(
    inst::TessInst
)::Union{Vector{Int}, Nothing}
```

画像から抽出された単語の信頼度を取得します。

**引数:**

| T   | 名前   | デフォルト | 説明                   |
|:--- |:---- |:----- |:-------------------- |
| R   | inst |       | 呼び出すTesseractインスタンス。 |

**詳細:**

このメソッドは、画像に対してまだ呼び出されていない場合、`tess_recognize()`を呼び出します。

**例:**

```jldoctest
using Tesseract

download_languages()

instance = TessInst()
pix = sample_pix()

tess_image(instance, pix)
tess_resolution(instance, 72)

confidence = tess_confidences(instance)

# 出力

256-element Vector{Int64}:
 95
 95
 92
 92
 96
 96
 96
 96
 96
 96
  ⋮
 96
 96
 96
 96
 96
 96
 96
 86
 86
```

参照: [`tess_tsv`](@ref), [`tess_parsed_tsv`](@ref)
