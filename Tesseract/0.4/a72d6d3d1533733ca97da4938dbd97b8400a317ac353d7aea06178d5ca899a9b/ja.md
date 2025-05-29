```
sample_pix()::Pix
```

テキストを含むサンプル画像を生成します。

**詳細:**

このメソッドの主な目的は、Tesseractライブラリの機能を示すために、Tesseractによって処理可能なテキストを含む画像のPixオブジェクトを提供することです。

この画像のテキストは、H.G.ウェルズの著書『宇宙戦争』の最初の段落です。この本はパブリックドメインにあるため、著作権は存在しません。

**例:**

```jldoctest
julia> using Tesseract

julia> update_languages()
true

julia> instance = TessInst()
Allocated Tesseract instance.

julia> pix = sample_pix()
Image (500, 600) at 32ppi

julia> tess_image(instance, pix)

julia> tess_resolution(instance, 72)

julia> text = tess_text(instance);
```

関連情報: [`sample_tiff`](@ref)
