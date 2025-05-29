```
tiles = Tiler(areawidth, areaheight, nrows, ncols, margin=20)
```

Tilerは、各イテレーションで次のタプルを返すイテレーターです：

  * 矩形空間（ページなど）を行と列に分割するタイルの中心の`x`/`y`ポイント（現在の0/0に対して相対的）
  * タイルの番号

`areawidth`と`areaheight`はタイルを配置する領域の寸法であり、`nrows`/`ncols`は必要な行と列の数、`margin`は関数が必要なタイルサイズを計算する前に領域の四つのエッジに適用されます。

TilerとPartitionは似ています：

  * Partitionはセルの幅と高さを指定できます
  * Tilerは必要なセルの行数と列数、そしてマージンを指定できます：

```julia
tiles = Tiler(1000, 800, 4, 5, margin=20)
for (pos, n) in tiles
    # ポイントposはタイルの中心です
end
```

計算されたタイルの幅と高さには、次のようにアクセスできます：

```julia
tiles = Tiler(1000, 800, 4, 5, margin=20)
for (pos, n) in tiles
    ellipse(pos.x, pos.y, tiles.tilewidth, tiles.tileheight, :fill)
end
```

現在どの行と列にいるかを知ることが時々役立ちます。`tiles.currentrow`と`tiles.currentcol`はその情報を提供します。

Tilerを使用してグリッドポイントを作成するには：

```julia
first.(collect(Tiler(800, 800, 4, 4)))
```

これはグリッドの中心点の配列を返します。
