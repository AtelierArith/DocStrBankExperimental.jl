```
HeatCuboid <: AbstractCubicObject
```

熱伝導のための二次元プレートのモデル

### 要素

`dimension` : プレートの長さ、幅、高さのタプル: (長さ, 幅, 高さ)

`sampling` : 空間離散化のタプル: (Δx, Δy, Δz)

`heatcells` : 合計の熱セルの数
