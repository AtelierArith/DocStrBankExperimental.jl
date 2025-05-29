```
visualize!(
    plt::AbstractPlot
    cpm::CellPotts;
    colorby=:type,
    cellcolors=nothing,
    migrationcolors=nothing,
    kwargs...)
```

CPMモデルの視覚化を生成します。

この関数は、与えられたプロットにセルラー・ポッツ・モデルの視覚化を追加します。
