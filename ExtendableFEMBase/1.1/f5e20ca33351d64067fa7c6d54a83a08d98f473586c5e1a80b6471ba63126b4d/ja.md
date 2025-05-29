```
abstract type HDIVRTkENRICH{k,edim} <: AbstractHdivFiniteElement where {edim<:Int}
```

内部（通常ゼロ）Hdiv準拠のベクトル値（ncomponents = edim）ラビアート・トーマス空間で、k ≥ 1の次数を持ち、追加の直交性の特性として、その発散がP_{k-edim+1}上でL2-直交しています。例：HDIVRTkENRICH{1,2}は三角形上のedim内部RT1バブル（＝法線トレースフリー）を提供し、その発散は積分平均ゼロです；HDIVRTkENRICH{2,2}は三角形上の3つのRT2バブルを提供し、その発散はすべてのP1関数に対してL2-直交しています。kの最大次数はTriangle2D（edim = 2）で4、Tetrahedron3D（edim = 3）で3です。これらの空間は単独では近似能力を持ちませんが、非圧縮性ストークス問題の発散フリー方式における強化空間として使用できます。

許可されるElementGeometries:

  * Triangle2D
  * Tetrahedron3D

```
