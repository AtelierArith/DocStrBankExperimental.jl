```
 extract_var(file::BatsrusHDF5Uniform, var::String; kwargs...)
```

HDF5 `file` から変数 `var` を抽出します。

# キーワード

  * `xmin`: x の最小抽出座標。
  * `xmax`: x の最大抽出座標。
  * `stepx`: x の抽出ストライド。
  * `ymin`: y の最小抽出座標。
  * `ymax`: y の最大抽出座標。
  * `stepy`: y の抽出ストライド。
  * `zmin`: z の最小抽出座標。
  * `zmax`: z の最大抽出座標。
  * `stepz`: z の抽出ストライド。
  * `verbose::Bool=true`: 出力変数の型とサイズ情報を表示します。
