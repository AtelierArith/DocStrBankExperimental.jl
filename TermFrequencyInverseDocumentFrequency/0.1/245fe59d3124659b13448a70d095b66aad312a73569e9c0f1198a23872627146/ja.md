```
normalize!(X)
```

スパース行列の各列を正規化して、`sum(X[:, j].^2) == 1` となるようにします。
