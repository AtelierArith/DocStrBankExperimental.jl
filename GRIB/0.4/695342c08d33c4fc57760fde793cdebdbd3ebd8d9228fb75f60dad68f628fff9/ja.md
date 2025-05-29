```
findmultiple(handle::Message, inlons::Vector{Float64}, inlats::Vector{Float64}; islsm=false)
```

各点に最も近い点を見つけます。

islsmをtrueに設定すると、最も近い陸地の点を見つけ、`handle`が陸海マスクを表す場合にのみ機能します。距離はキロメートル単位です。

# 例

```Julia
lons, lats, values, distances = findmultiple(handle, inlons, inlats)
```
