```
tess_resolution(
    inst::TessInst, # 設定するインスタンス。
    ppi             # ソース画像のPPI。
)::Nothing
```

画像の解像度をppiで設定します。

**引数:**

| T   | 名前   | デフォルト | 説明                       |
|:--- |:---- |:----- |:------------------------ |
| R   | inst |       | 画像を読み込むインスタンス。           |
| R   | ppi  |       | ソース画像のPPI（インチあたりのピクセル数）。 |

**例:**

```jldoctest
julia> using Tesseract

julia> download_languages()
true

julia> instance = TessInst()
Tesseractインスタンスを割り当てました。

julia> pix = sample_pix()
画像 (500, 600) at 32ppi

julia> tess_image(instance, pix)

julia> tess_resolution(instance, 72)
```

関連情報: [`tess_image`](@ref)
