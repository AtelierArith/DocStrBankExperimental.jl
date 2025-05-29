```
function NodalInterpolator(FES::FESpace{T}, grid = FES.dofgrid; broken = FES.broken, component_offset = FES.coffset, kwargs...)
```

要求されたノード（アイテム）のグリッドで関数を評価するevaluate!関数を持つ補間器構造体を構築します。壊れたモードでは、ON_CELLのアイテムはセルを参照し、これらのセルのすべてのノードが評価されます。
