```
edgeplot(paths::Vector{AbstractPath})
edgeplot!(sc, paths::Vector{AbstractPath})
```

エッジを描画するためのレシピ。属性 `plottype` はどちらかである必要があります。もし `eltype(pathes) <: Line` であれば、`linesegments` を使用して描画します。もし `<:AbstractPath` であれば、ベジエセグメントを使用して描画します。すべての属性は実際のレシピに渡されます。
