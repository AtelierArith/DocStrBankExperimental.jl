```
fits_write_pixnull(f::FITSFile, data::StridedArray, nulval)
```

配列 `data` 全体を FITS ファイルに書き込みます。引数 `nulval` は「ヌル値」と見なされる値を指定し、`data` の要素タイプに対応する適切な数値に置き換えられます。

!!! note
    `data` はメモリ内に連続して格納される必要があります。


参照: [`fits_write_pix`](@ref)
