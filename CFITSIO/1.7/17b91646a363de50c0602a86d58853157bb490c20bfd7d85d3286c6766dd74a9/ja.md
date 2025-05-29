```
fits_open_data(filename::String, [mode = 0])
```

既存のデータファイル（[`fits_open_file`](@ref)のような）を開き、画像またはテーブルを含む最初のHDUに移動します。

## モード:

  * 0 : 読み取り専用（`CFITSIO.R`で同等に示される）
  * 1 : 読み書き（`CFITSIO.RW`で同等に示される）
