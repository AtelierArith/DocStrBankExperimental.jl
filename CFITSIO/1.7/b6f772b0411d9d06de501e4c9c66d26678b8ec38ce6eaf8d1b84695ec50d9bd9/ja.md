```
fits_get_img_type(f::FITSFile)
```

現在の画像HDUのデータ型（bitpix）を返します。これは、関数[`type_from_bitpix`](@ref)を使用してJulia型に変換できます。
