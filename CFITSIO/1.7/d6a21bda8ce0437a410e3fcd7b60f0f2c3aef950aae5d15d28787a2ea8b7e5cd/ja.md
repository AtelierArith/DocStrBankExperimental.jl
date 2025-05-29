```
fits_delete_hdu(f::FITSFile)
```

FITSファイルからHDUを削除し、次のHDUを前方にシフトします。`f`がファイル内のプライマリHDUである場合、データがなく最小限のヘッダー情報を持つヌルプライマリHDUに置き換えられます。

新しい現在のHDUのタイプを示すシンボルを返します。可能なシンボルは、`image_hdu`、`ascii_table`、または`binary_table`です。`hduNum`の値は、1から[`fits_get_num_hdus`](@ref)によって返される値の範囲内でなければなりません。
