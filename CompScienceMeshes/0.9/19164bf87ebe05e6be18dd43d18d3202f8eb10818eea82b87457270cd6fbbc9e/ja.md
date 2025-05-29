```
numvertices(mesh)
```

メッシュ内の頂点の数を返します。

*注*: これは頂点バッファ内の頂点の数であり、浮遊頂点やセルに表示されない頂点を含む可能性があります。言い換えれば、以下は必ずしも真ではありません：

```julia
    numvertices(mesh) == numcells(skeleton(mesh,0))
```
