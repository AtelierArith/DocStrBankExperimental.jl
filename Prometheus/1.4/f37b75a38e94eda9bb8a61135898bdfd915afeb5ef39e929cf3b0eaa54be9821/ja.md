```
Prometheus.observe(histogram::Histogram, v::Real)
```

ヒストグラムに観測値 `v` を追加します。これにより、ヒストグラムの合計とカウントがそれぞれ `v` と `1` 増加し、`v` を含むすべてのバケットのカウンターがインクリメントされます。
