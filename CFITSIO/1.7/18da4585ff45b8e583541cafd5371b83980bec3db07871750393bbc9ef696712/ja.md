```
fits_write_pix(f::FITSFile, data::StridedArray)
```

配列 `data` 全体を FITS ファイルに書き込みます。

!!! note
    `data` はメモリ内に連続して格納されている必要があります。


参照: [`fits_write_pixnull`](@ref), [`fits_write_subset`](@ref)
