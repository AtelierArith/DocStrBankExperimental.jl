```
sample_tiff()::Vector{UInt8}
```

テキストを含むTIFF画像のバイト配列を生成します。

**詳細:**

このメソッドの主な目的は、Tesseractライブラリの機能を示すために、Tesseractによって処理可能なテキストを含む画像のバイトストリームを提供することです。

この画像のテキストは、H.G.ウェルズの著書『世界の戦争』の最初の段落です。この本はパブリックドメインにあるため、著作権は存在しません。

**例:**

```jldoctest
julia> using Tesseract

julia> data = sample_tiff();

julia> pix = pix_read_tiff(data)
Image (500, 600) at 32ppi
```

参照: [`sample_pix`](@ref)
