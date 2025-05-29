```
@enum IFF begin
    IFF_UNKNOWN        = 0
    IFF_BMP            = 1
    IFF_JFIF_JPEG      = 2
    IFF_PNG            = 3
    IFF_TIFF           = 4
    IFF_TIFF_PACKBITS  = 5
    IFF_TIFF_RLE       = 6
    IFF_TIFF_G3        = 7
    IFF_TIFF_G4        = 8
    IFF_TIFF_LZW       = 9
    IFF_TIFF_ZIP       = 10
    IFF_PNM            = 11
    IFF_PS             = 12
    IFF_GIF            = 13
    IFF_JP2            = 14
    IFF_WEBP           = 15
    IFF_LPDF           = 16
    IFF_TIFF_JPEG      = 17
    IFF_DEFAULT        = 18
    IFF_SPIX           = 19
end
```

leptonicaによって画像タイプを指定するために使用されるさまざまな定数。

**詳細:**

| 値                 | 説明                   |
|:----------------- |:-------------------- |
| IFF_UNKNOWN       | 不明な画像タイプ。            |
| IFF_BMP           | BMP画像。               |
| IFF*JFIF*JPEG     | JPEG画像。              |
| IFF_PNG           | PNG画像。               |
| IFF_TIFF          | 圧縮のないTIFF画像。         |
| IFF*TIFF*PACKBITS | パックビット圧縮のTIFF画像。     |
| IFF*TIFF*RLE      | RLE圧縮のTIFF画像。        |
| IFF*TIFF*G3       | G3圧縮のTIFF画像。         |
| IFF*TIFF*G4       | G4圧縮のTIFF画像。         |
| IFF*TIFF*LZW      | LZW圧縮のTIFF画像。        |
| IFF*TIFF*ZIP      | ZIP圧縮のTIFF画像。        |
| IFF_PNM           | PNM画像。               |
| IFF_PS            | PostScriptファイル。      |
| IFF_GIF           | GIF画像。               |
| IFF_JP2           | JP2K画像。              |
| IFF_WEBP          | WEBP画像。              |
| IFF_LPDF          | PDFファイル。             |
| IFF*TIFF*JPEG     | JPEG圧縮のTIFF画像。       |
| IFF_DEFAULT       | デフォルトの画像タイプ（保存時に使用）。 |
| IFF_SPIX          | SPIX画像。              |
