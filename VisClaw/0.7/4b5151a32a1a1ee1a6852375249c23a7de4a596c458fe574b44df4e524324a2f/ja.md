```
eta_uniformgrid = interpsurface(amrgrid::Vector{VisClaw.AMRGrid}, topo::VisClaw.Topo)
eta_uniformgrid = interpsurface(amr::VisClaw.AMR, topo::VisClaw.Topo)
```

SciPyの散発的補間を使用してAMRタイルデータを均一グリッドデータに変換します。

浸水高さ（陸）の補間はサポートされていません。
