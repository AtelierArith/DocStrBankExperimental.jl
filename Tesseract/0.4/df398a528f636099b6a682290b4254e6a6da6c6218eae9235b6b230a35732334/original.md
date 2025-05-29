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

Various constants used by leptonica to specify image types.

**Details:**

| Value             | Description                            |
|:----------------- |:-------------------------------------- |
| IFF_UNKNOWN       | Unknown image type.                    |
| IFF_BMP           | BMP image.                             |
| IFF*JFIF*JPEG     | JPEG image.                            |
| IFF_PNG           | PNG image.                             |
| IFF_TIFF          | TIFF image with no compression.        |
| IFF*TIFF*PACKBITS | TIFF image with pack bits compression. |
| IFF*TIFF*RLE      | TIFF image with RLE compression.       |
| IFF*TIFF*G3       | TIFF image with G3 compression.        |
| IFF*TIFF*G4       | TIFF image with G4 compression.        |
| IFF*TIFF*LZW      | TIFF image with LZW compression.       |
| IFF*TIFF*ZIP      | TIFF image with ZIP compression.       |
| IFF_PNM           | PNM image.                             |
| IFF_PS            | PostScript file.                       |
| IFF_GIF           | GIF image.                             |
| IFF_JP2           | JP2K image.                            |
| IFF_WEBP          | WEBP image.                            |
| IFF_LPDF          | PDF file.                              |
| IFF*TIFF*JPEG     | TIFF image with JPEG compression.      |
| IFF_DEFAULT       | Default image type (used in saving).   |
| IFF_SPIX          | SPIX image.                            |
