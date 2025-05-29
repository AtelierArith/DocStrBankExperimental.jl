```
p = Partition(areawidth, areaheight, tilewidth, tileheight)
```

Partitionは、各イテレーションで次のタプルを返すイテレーターです：

  * 矩形空間（ページなど）を行と列に分割するタイルの中心の`x`/`y`ポイント（現在の0/0に対して相対的）
  * タイルの番号

`areawidth`と`areaheight`はタイルを配置する領域の寸法であり、`tilewidth`/`tileheight`はタイルの寸法です。

TilerとPartitionは似ています：

  * Partitionはセルの幅と高さを指定できます
  * Tilerはセルの行と列の数、及びマージンを指定できます

    ```julia
    tiles = Partition(1200, 1200, 30, 30)
    for (pos, n) in tiles

        # ポイントposはタイルの中心です

    end
    ```

計算されたタイルの幅と高さには、次のようにアクセスできます：

```julia
tiles = Partition(1200, 1200, 30, 30)
for (pos, n) in tiles
    ellipse(pos.x, pos.y, tiles.tilewidth, tiles.tileheight, :fill)
end
```

現在いる行と列を知ることができるのは時々便利です：

```
tiles.currentrow
tiles.currentcol
```

これらはその情報を提供します。

タイルの幅と高さが領域の幅と高さの正確な倍数でない限り、タイルが収まらない右側と下側に境界が表示されます。
