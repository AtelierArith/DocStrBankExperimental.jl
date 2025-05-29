```
tess_image(
        inst::TessInst,
        pix::Pix
    )::Nothing
```

OCRされる画像を設定します。

**引数:**

| T   | 名前   | デフォルト | 説明                           |
|:--- |:---- |:----- |:---------------------------- |
| R   | inst |       | 画像を読み込むインスタンス。               |
| R   | pix  |       | TesseractにOCRを実行するために読み込む画像。 |

**詳細:**

1つの画像のみ設定可能で、これを複数回呼び出すと最後の画像が置き換えられます。

**例:**

```jldoctest
julia> using Tesseract

julia> download_languages()
true

julia> instance = TessInst()
Allocated Tesseract instance.

julia> pix = sample_pix()
Image (500, 600) at 32ppi

julia> tess_image(instance, pix)
```

参照: [`tess_resolution`](@ref), [`pix_read`](@ref)
