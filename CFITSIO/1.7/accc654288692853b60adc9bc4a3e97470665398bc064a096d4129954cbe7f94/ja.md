```
fits_open_file(filename::String, [mode = 0])
```

既存のデータファイルを開きます。

## モード:

  * 0 : 読み取り専用 (同等に `CFITSIO.READONLY` または `CFITSIO.R` と表記されます)
  * 1 : 読み書き (同等に `CFITSIO.READWRITE` または `CFITSIO.RW` と表記されます)

この関数は拡張ファイル名構文を使用してファイルを開きます。拡張ファイル名パーサーを使用せず、`filename` をそのままファイル名として使用する [`fits_open_diskfile`](@ref) も参照してください。
