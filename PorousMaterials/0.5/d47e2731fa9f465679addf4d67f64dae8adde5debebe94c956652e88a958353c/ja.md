```
write_cube(grid, filename, verbose=true)
```

グリッドを .cube ファイル形式に書き込みます。この形式については、こちらを参照してください: http://paulbourke.net/dataformats/cube/ 単位セルの原子は .cube には印刷されません。代わりに、原子を視覚化するために .xyz ファイルを使用してください。

# 引数

  * `grid::Grid`: 各グリッドポイントに関連付けられたデータを持つグリッド。
  * `filename::AbstractString`: グリッドを書き込む .cube ファイルの名前; これは `rc[:paths][:grids]` に対して相対的です。
  * `verbose::Bool`: 書き込み後にファイル名を印刷します。
  * `length_units::String`: 長さの単位。ボーアまたはオングストローム。
