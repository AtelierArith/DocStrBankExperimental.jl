```
write_mtg(file, mtg; kwargs...)
write_mtg(file, mtg, classes, description, features)
```

ディスクにmtgファイルを書き込みます。

# 引数

  * `file::String`: 書き込むMTGファイルのパス。
  * `mtg`: mtg
  * `classes`: クラスセクション
  * `description`: 説明セクション
  * `features`: 特徴セクション

# 注意

kwargsを使用して、すべての代わりにクラス、説明、特徴のゼロ、1、または2を指定できます。この場合、欠落しているものは[`get_classes`](@ref)、[`get_features`](@ref)または[`get_description`](@ref)を使用して再計算されます。

# 例

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)
write_mtg("test.mtg",mtg)
```
