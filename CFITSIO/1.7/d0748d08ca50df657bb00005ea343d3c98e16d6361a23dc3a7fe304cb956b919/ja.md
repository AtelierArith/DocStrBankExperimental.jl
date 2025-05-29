```
fits_open_image(filename::String, [mode = 0])
```

既存のデータファイル（[`fits_open_file`](@ref)のような）を開き、画像を含む最初のHDUに移動します。

## モード:

  * 0 : 読み取り専用（`CFITSIO.READONLY`または`CFITSIO.R`で同等に示されます）
  * 1 : 読み書き（`CFITSIO.READWRITE`または`CFITSIO.RW`で同等に示されます）
