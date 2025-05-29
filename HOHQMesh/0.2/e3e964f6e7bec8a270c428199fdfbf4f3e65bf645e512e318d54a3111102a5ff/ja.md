```
addBackgroundGrid!(proj::Project, x0::Array{Float64}, dx::Array{Float64}, N::Array{Int})
```

左隅 x0、グリッドサイズ dx、および各方向の区間数 N を使用して背景グリッドブロックを追加します。モデルに外部境界が定義されていない場合にこれを使用します。このバージョンは HOHQMesh の backgroundGrid ブロックを模倣していますが、次のバージョン

```
addBackgroundGrid!(proj::Project, box::Array{Float64},  N::Array{Int} )
```

ははるかに使いやすいです。

TODO: HOHQMesh を変更し、この方法で領域を指定するのを削除し、代わりにバウンディングボックスのものを使用します。
