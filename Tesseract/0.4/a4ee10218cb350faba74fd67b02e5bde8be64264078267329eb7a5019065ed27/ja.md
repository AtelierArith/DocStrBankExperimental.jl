```
tess_recognize(
    inst::TessInst
)::Bool
```

OCR抽出を実行します。これは、取得関数のいずれかを呼び出すと自動的に呼び出されるため、直接呼び出す必要はありません。エラーが発生した場合は`false`を返します。

**引数:**

|   T | 名前   | デフォルト | 説明                |
| ---:|:---- |:----- |:----------------- |
|   R | inst |       | 認識を実行するためのインスタンス。 |

**例:**

```jldoctest
julia> using Tesseract

julia> download_languages("eng+fra")
true

julia> instance = TessInst("eng+fra")
Allocated Tesseract instance.

julia> pix = sample_pix()
Image (500, 600) at 32ppi

julia> tess_image(instance, pix)

julia> tess_resolution(instance, 72)

julia> tess_recognize(instance)
true
```

参照: [`tess_text`](@ref), [`tess_hocr`](@ref), [`tess_alto`](@ref), [`tess_tsv`](@ref), [`tess_parsed_tsv`](@ref).
