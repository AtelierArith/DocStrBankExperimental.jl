```
colorbar(parent, plotobject, kwargs...)
```

プロットを色付けするために選択した属性に基づいてカラーバーを追加します。plotobjectは属性によって色付けされたMTGのプロットでなければなりません。他の使用ケースにはMakie.Colorbarを使用してください。

# 引数

  * `parent`: 親シーン
  * `plotobject`: カラーバーを追加するプロットオブジェクト
  * `kwargs`: Makie.Colorbarに渡すキーワード引数、*例* `label="Length (m)"`

# 例

```julia
using GLMakie, MultiScaleTreeGraph, PlantGeom
file = joinpath(dirname(dirname(pathof(PlantGeom))), "test", "files", "simple*plant.opf")
opf = read*opf(file)

f, ax, p = viz(opf, color=:Length)
colorbar(f[1, 2], p)
f
```
