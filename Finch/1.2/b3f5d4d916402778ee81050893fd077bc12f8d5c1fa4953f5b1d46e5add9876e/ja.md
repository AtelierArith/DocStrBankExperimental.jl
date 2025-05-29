bspread(::AbstractString) bspread(::HDF5.File) bspread(::NPYPath)

[Binsparse](https://github.com/GraphBLAS/binsparse-specification)ファイルをFinchテンソルに読み込みます。

サポートされているファイル拡張子は次のとおりです：

  * `.bsp.h5`: HDF5ファイル形式（[HDF5](https://github.com/JuliaIO/HDF5.jl)をロードする必要があります）
  * `.bspnpy`: NumPyおよびJSONディレクトリ形式（[NPZ](https://github.com/fhs/NPZ.jl)をロードする必要があります）

!!! warning



Binsparse仕様は開発中です。さらに、この関数は完全に準拠していない可能性があります。何か問題があればバグレポートを提出してください。
