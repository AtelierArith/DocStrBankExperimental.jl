```
fused_rings(mol::SimpleMolGraph{T}) -> Vector{Vector{T}}
```

融合環ノードセットのベクトルを返します。

融合環は、グラフ理論の観点から2辺連結成分として定義されます。スピロ環構造は融合環の一部と見なされます。
