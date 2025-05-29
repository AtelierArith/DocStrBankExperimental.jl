```
find(near::Nearest, handle::Message, inlon::Float64, inlat::Float64; samepoint=true, samegrid=true)
```

与えられた点に最も近い4つの点を距離でソートして見つけます。

samepointとsamegridをtrue（デフォルト）に設定すると、計算が速くなりますが、呼び出しごとに点とグリッドが変更されるのを制限します。距離はキロメートル単位です。

# 例

```Julia
Nearest(handle) do near
    lons, lats, values, distances = find(near, handle, inlon, inlat)
end
```
