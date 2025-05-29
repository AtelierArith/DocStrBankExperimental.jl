```
bw_opt_kde(pts, test_pts; test_low=-1, test_high=1)
```

は、`pts` に基づいて、`test_pts` の尤度を最大化するバンド幅ファクターを持つKDEを返します。

`test_low` と `test_high` は、最適化検索のためのバンド幅ファクターの自然対数の範囲です。
