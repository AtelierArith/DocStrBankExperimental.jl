```
tess_parsed_tsv(
    inst::TessInst,
    page::Integer = Int32(1)
)::Union{Vector{Tsv}, Nothing}
```

認識からTSV結果を取得し、それをTsvオブジェクトのリストに解析します。エラーが発生した場合は何も返しません。

**引数:**

| T   | 名前   | デフォルト      | 説明                |
|:--- |:---- |:---------- |:----------------- |
| R   | inst |            | 呼び出すテッセラクトインスタンス。 |
| O   | page | `Int32(1)` | データを取得するページ。      |

**例:**

```jldoctest
using Tesseract

download_languages()

instance = TessInst()
pix = sample_pix()

tess_image(instance, pix)
tess_resolution(instance, 72)

tsv = tess_parsed_tsv(instance);

# 出力

292-element Vector{Tsv}:
 Page:  [1] (500, 600)
 Block: [1/1] (10, 9) - (479, 514)
 Para:  [1/1/1] (11, 9) - (406, 14)
 Line:  [1/1/1/1] (11, 9) - (406, 14)
 Word:  [1/1/1/1/1] No (95.79193%)
 Word:  [1/1/1/1/2] one (95.79193%)
 Word:  [1/1/1/1/3] would (92.95379%)
 Word:  [1/1/1/1/4] have (92.95379%)
 Word:  [1/1/1/1/5] believed (96.81915%)
 Word:  [1/1/1/1/6] in (96.770004%)
 ⋮
 Word:  [1/1/7/3/5] twentieth (96.62509%)
 Word:  [1/1/7/3/6] century (96.81123%)
 Word:  [1/1/7/3/7] came (96.81123%)
 Word:  [1/1/7/3/8] the (96.72949%)
 Word:  [1/1/7/3/9] great (96.72949%)
 Para:  [1/1/8] (11, 509) - (172, 14)
 Line:  [1/1/8/1] (11, 509) - (172, 14)
 Word:  [1/1/8/1/1] great (86.34806%)
 Word:  [1/1/8/1/2] disillusionment. (86.34806%)
```

参照: [`tess_tsv`](@ref), [`tess_confidences`](@ref)
