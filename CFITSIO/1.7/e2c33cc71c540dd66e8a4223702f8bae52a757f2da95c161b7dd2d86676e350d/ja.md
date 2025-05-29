```
fits_open_diskfile(filename::String, [mode = 0])
```

既存のデータファイルを開きます。

## モード:

  * 0 : 読み取り専用（`CFITSIO.READONLY`または`CFITSIO.R`で同等に表されます）
  * 1 : 読み書き（`CFITSIO.READWRITE`または`CFITSIO.RW`で同等に表されます）

この関数は拡張ファイル名パーサーを使用せず、`filename`をそのまま開くファイルの名前として使用します。拡張ファイル名構文を使用する[`fits_open_file`](@ref)も参照してください。
