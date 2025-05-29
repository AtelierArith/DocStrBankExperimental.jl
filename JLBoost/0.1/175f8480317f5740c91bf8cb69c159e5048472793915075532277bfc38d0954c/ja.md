```
find_best_split(loss, feature, target, warmstart, lambda, gamma)
```

最適な（バイナリ）スプリットポイントを、∑ loss(warmstart + δx, target)を2次テイラー級数展開を用いて最適化することで見つけます。

Feature、target、およびwarmstartがソートされているとは仮定せず、それらをソートします。
