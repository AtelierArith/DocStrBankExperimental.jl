```
vtk2trixi(file::String)
```

VTKファイルを読み込み、データを[`InitialCondition`](@ref)に変換します。

# 引数

  * `file`: 読み込むVTKファイルの名前。

!!! warning "実験的な実装"
    これは実験的な機能であり、将来のリリースで変更される可能性があります。


# 例

```jldoctest; output = false

# 長方形の形状を作成

rectangular = RectangularShape(0.1, (10, 10), (0, 0), density=1.5, velocity=(1.0, -2.0),                                pressure=1000.0)

# `InitialCondition`をvtkファイルに書き込む

trixi2vtk(rectangular; filename="rectangular", output_directory="out")

# vtkファイルを読み込み、`InitialCondition`に変換する

ic = vtk2trixi(joinpath("out", "rectangular.vtu"))

# 出力

┌──────────────────────────────────────────────────────────────────────────────────────────────────┐ │ InitialCondition{Float64}                                                                        │ │ ═════════════════════════                                                                        │ │ #dimensions: ……………………………………………… 2                                                                │ │ #particles: ………………………………………………… 100                                                              │ │ particle spacing: ………………………………… 0.1                                                              │ └──────────────────────────────────────────────────────────────────────────────────────────────────┘
```
