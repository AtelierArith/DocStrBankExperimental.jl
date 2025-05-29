```
pairplot(gridpos::Makie.GridPosition, inputs...; kwargs...)
```

指定されたMakie図のグリッド位置にペアプロットを作成します。

例

```julia
fig = Figure()
pairplot(fig[2,3], table)
fig
```
