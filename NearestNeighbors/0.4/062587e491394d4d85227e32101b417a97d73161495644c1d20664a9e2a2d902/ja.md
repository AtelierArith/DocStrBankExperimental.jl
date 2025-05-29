```
KDTree(data [, metric = Euclidean(); leafsize = 25, reorder = true]) -> kdtree
```

与えられた `metric` と `leafsize` を使用してデータから `KDTree` を作成します。`metric` は `MinkowskiMetric` でなければなりません。
