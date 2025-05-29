```
place_diatomics(n_molecules, boundary, bond_length; min_dist=nothing,
                max_attempts=100, aligned=false, rng=Random.default_rng())
```

ランダムな二原子分子の座標を生成します。

境界ボックス `boundary` 内で `n_molecules` の二原子分子の座標を取得します。ここで、2つの点が `min_dist` より近くならず、結合長が `bond_length` であることを考慮し、周期境界条件を考慮します。キーワード引数 `max_attempts` は、原子の配置を停止する失敗した試行の回数を決定します。キーワード引数 `aligned` は、結合がすべて同じ方向を指すか（`true`）、ランダムな方向を指すか（`false`）を決定します。1つ以上の次元に無限の境界がある場合は使用できません。
