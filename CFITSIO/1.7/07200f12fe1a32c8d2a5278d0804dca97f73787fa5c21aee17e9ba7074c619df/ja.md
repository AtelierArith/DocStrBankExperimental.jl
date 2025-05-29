```
fits_movabs_hdu(f::FITSFile, hduNum::Integer)
```

現在のHDUを`hduNum`で指定された値に変更し、HDUのタイプを示すシンボルを返します。

可能なシンボルは、`image_hdu`、`ascii_table`、または`binary_table`です。`hduNum`の値は、[`fits_get_num_hdus`](@ref)によって返される値の範囲内で1からの範囲でなければなりません。
