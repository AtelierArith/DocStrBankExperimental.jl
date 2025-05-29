```
struct ProjectionPoint
    Lon     :: Float64
    Lat     :: Float64
    EW      :: Float64
    NS      :: Float64
    zone    :: Integer
    isnorth :: Bool
end
```

Lon/Latからデカルトグリッドへのデータセットを投影するために使用される点の座標を保持する構造体。
