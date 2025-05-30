```
HeatPlate <: AbstractCubicObject
```

熱伝導のための二次元プレートのモデル

### 要素

`dimension` : プレートの長さと幅のタプル: (長さ, 幅)

`sampling` : 空間離散化のタプル: (Δx, Δy)

`heatcells` : 各方向のヒートセルの数: {Nx, Ny}
