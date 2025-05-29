```
blend(centerpos1, rad1, centerpos2, rad2, color1, color2)
```

放射状のブレンドを作成します。

例:

```julia
redblue = blend(
    pos, 0,                   # 最初の円の中心と半径
    pos, tiles.tilewidth/2,   # 2番目の円の中心と半径
    "red",
    "blue",
)
```
