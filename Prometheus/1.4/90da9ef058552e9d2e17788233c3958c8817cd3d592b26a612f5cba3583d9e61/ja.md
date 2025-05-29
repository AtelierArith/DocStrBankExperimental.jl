```
Prometheus.observe(summary::Summary, v::Real)
```

観測された値 `v` をサマリーに追加します。これにより、サマリーの合計とカウントがそれぞれ `v` と `1` 増加します。
