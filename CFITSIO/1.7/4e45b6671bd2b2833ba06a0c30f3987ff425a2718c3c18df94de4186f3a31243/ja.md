```
fits_create_file(filename::AbstractString)
```

新しい空の出力 `FITSFile` を作成して開きます。このメソッドは、[拡張ファイル名構文](https://heasarc.gsfc.nasa.gov/docs/software/fitsio/c/c_user/node83.html) を使用してファイルを作成します。

また、拡張ファイル名パーサーを使用しない [`fits_create_diskfile`](@ref) も参照してください。
