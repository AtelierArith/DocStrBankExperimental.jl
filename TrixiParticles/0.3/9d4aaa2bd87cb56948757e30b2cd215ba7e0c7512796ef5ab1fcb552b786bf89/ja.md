```
trixi2vtk(coordinates; output_directory="out", prefix="", filename="coordinates",
          custom_quantities...)
```

座標データをVTK形式に変換します。

# 引数

  * `coordinates`: 保存する座標。

# キーワード

  * `output_directory="out"`: 出力ディレクトリのパス。
  * `prefix=""`:              出力ファイルのプレフィックス。
  * `filename="coordinates"`: 出力ファイルの名前。
  * `custom_quantities...`:   VTK出力に含める追加のカスタム量。

# 戻り値

  * `file::AbstractString`: 生成されたVTKファイルへのパス。
