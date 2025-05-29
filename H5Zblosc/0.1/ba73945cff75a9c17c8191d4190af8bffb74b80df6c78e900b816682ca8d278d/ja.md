```
BloscFilter(;level=5, shuffle=true, compressor="blosclz")
```

Blosc圧縮フィルタ、[Blosc.jl](https://github.com/JuliaIO/Blosc.jl)を使用しています。オプション：

  * `level`: 圧縮レベル
  * `shuffle`: 圧縮前にデータをシャッフルするかどうか（このオプションは[`Shuffle`](@ref)フィルタの代わりに使用するべきです）
  * `compressor`: 圧縮アルゴリズム。利用可能な圧縮器については`Blosc.compressors()`を呼び出してください。

# 外部リンク

  * [What Is Blosc?](https://www.blosc.org/pages/blosc-in-depth/)
  * [Blosc HDF5 Filter ID 32001](https://portal.hdfgroup.org/display/support/Filters#Filters-32001)
  * [Blosc HDF5 Plugin Repository (C code)](https://github.com/Blosc/hdf5-blosc)
