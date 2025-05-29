```
place_atoms(n_atoms, boundary; min_dist=nothing, max_attempts=100, rng=Random.default_rng())
```

ランダム座標を生成します。

周期境界条件を考慮しながら、`min_dist` より近くにない `n_atoms` の座標を境界ボックス `boundary` 内に取得します。キーワード引数 `max_attempts` は、原子の配置を停止するまでの失敗した試行の回数を決定します。一つ以上の次元に無限の境界がある場合は使用できません。
