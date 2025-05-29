```
trixi2vtk(initial_condition::InitialCondition; output_directory="out",
          prefix="", filename="initial_condition", custom_quantities...)
```

[`InitialCondition`](@ref) データを VTK 形式に変換します。

# 引数

  * `initial_condition`: 保存する [`InitialCondition`](@ref)。

# キーワード

  * `output_directory="out"`: 出力ディレクトリのパス。
  * `prefix=""`:              出力ファイルのプレフィックス。
  * `filename="coordinates"`: 出力ファイルの名前。
  * `custom_quantities...`:   VTK 出力に含める追加のカスタム量。

# 戻り値

  * `file::AbstractString`: 生成された VTK ファイルへのパス。
