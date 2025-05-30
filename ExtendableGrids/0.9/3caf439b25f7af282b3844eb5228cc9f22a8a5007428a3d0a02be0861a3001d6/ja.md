```
rect!(grid,maskmin,maskmax; 
      region=1, 
      bregion=1, 
      bregions=nothing, 
      tol=1.0e-10)
```

長方形を長方形のグリッドに配置します。`maskmin`と`maskmax`に従ってセルマスクを配置し、マスク領域のすべての側面に`bfacesmask!`を介して境界面を導入します。マスク内の座標値がグリッドの対応する方向の座標と一致すること（許容範囲内）が確認されます。

`bregions`が指定されている場合、それは1Dの`w,e`、2Dの`s,e,n,w`、3Dの`s,e,n,w,b,t`の順序に対応する側面の数に対応するベクトルであると見なされます。

`bregion`または`bregions`の要素は数値または関数`ireg(current_region)`であることができます。

例: [Subgrid-from-rectangle](@ref), [Rect2d-with-bregion-function](@ref),  [Cross3d](@ref)
