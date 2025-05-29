```
get_nonoverlapping_periods(dfo::DataFrame)
```

重複しない期間を取得します。

# 引数

  * `dfo`: `p_start` と `p_end` の列を持つ DataFrame で、`p_start` が増加するようにソートされています。

# 値

  * `p_start[i] > p_end[i-1]` を満たす `p_start` と `p_end` の列を持つ DataFrame。
