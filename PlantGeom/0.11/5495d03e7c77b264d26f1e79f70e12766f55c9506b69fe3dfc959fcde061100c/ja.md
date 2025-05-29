```
diagram(opf::MultiScaleTreeGraph.Node; kwargs...)
diagram!(opf::MultiScaleTreeGraph.Node; kwargs...)
```

MTGツリーの図を`Makie.jl`バックエンドを使用して作成します。

!!! danger
    この関数はパッケージの拡張です。`using PlantGeom`の前にMakieバックエンド（*例*：`using GLMakie`）をインポートした場合にのみ利用可能です。


主な属性は次のとおりです：

  * color: ノードの色
  * colormap: 色が属性を使用する場合に使用されるカラーマップ。デフォルトではviridisを使用します。

[ColorSchemes](https://juliagraphics.github.io/ColorSchemes.jl/stable/basics/)からのColorSchemeであるか、名前を持つSymbolでなければなりません。

# 例

```julia
using GLMakie, PlantGeom

file = joinpath(dirname(dirname(pathof(PlantGeom))),"test","files","simple_plant.opf")
# file = joinpath(dirname(dirname(pathof(PlantGeom))),"test","files","coffee.opf")

opf = read_opf(file)

diagram(opf)

# さまざまなオプションで3Dプロットに色を付けることもできます：
# 1つの共有色で：
diagram(opf, color = :red)

# またはopf属性によって色付けする、*例*：ノードのZ座標を使用：
diagram(opf, color = :ZZ)
```
