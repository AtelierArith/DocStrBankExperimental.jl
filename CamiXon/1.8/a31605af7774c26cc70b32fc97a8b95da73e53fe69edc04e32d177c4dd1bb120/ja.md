```
collectSpinorbit(config::String; msg=false)
```

`config`（標準構成表記で指定された）によって指定されたスピン軌道をスピン軌道の配列に集めます。

#### 例:

```
julia> config = "1s²2s²2p⁶";

julia> collectSpinorbit(config; msg=true)
10-element Vector{Spinorbit}:
 Spinorbit("1s↓", 1, 0, 0, 0, -1//2)
 Spinorbit("1s↑", 1, 0, 0, 0, 1//2)
 Spinorbit("2s↓", 2, 1, 0, 0, -1//2)
 Spinorbit("2s↑", 2, 1, 0, 0, 1//2)
 Spinorbit("2p↓", 2, 0, 1, -1, -1//2)
 Spinorbit("2p↓", 2, 0, 1, 0, -1//2)
 Spinorbit("2p↓", 2, 0, 1, 1, -1//2)
 Spinorbit("2p↑", 2, 0, 1, -1, 1//2)
 Spinorbit("2p↑", 2, 0, 1, 0, 1//2)
 Spinorbit("2p↑", 2, 0, 1, 1, 1//2)
```
