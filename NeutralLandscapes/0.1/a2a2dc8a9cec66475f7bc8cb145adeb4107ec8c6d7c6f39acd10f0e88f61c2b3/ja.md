```
normalize(mats::Vector{M})
```

中立的風景のベクトル `mats` を正規化し、すべての値を0と1の間にします。この操作は、特定の `NeutralLandscapeUpdater` に対する `rate` パラメータを保持せず、代わりにすべての `mats` にわたる総最大値と総最小値の差に比例して再スケーリングします。
