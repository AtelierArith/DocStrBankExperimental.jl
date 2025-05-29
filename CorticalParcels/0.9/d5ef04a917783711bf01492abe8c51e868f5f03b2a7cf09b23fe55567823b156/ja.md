```
dilate!(p, A; limit = nothing)
```

`Parcel` `p` に対して、隣接行列 `A` に基づいて1回の膨張を実行します。オプションで、追加できる新しい頂点の数に対する `limit::Int` を指定できます。
