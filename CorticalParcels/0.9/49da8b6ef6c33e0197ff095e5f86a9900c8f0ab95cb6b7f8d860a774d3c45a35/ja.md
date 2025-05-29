```
erode!(p, neighbors; limit = nothing)
```

`Parcel` `p` に対して、隣接リスト `neighbors` に基づいて単一の侵食を実行します。オプションで、削除したい頂点の数に対する `limit::Int` を指定できます。
