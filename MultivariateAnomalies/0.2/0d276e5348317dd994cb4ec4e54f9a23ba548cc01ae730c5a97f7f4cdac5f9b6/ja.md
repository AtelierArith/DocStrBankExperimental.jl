```
get_quantile_scores(scores, quantiles = 0.0:0.01:1.0)
```

与えられた N 次元異常 `scores` キューブの分位数を返します。`quantiles`（デフォルト: `quantiles = 0.0:0.01:1.0`）は分位数の Float 範囲です。任意のスコアが `quantiles[i]` 以上であり、`quantiles[i+1]` 未満である場合、そのスコアはそれぞれの分位数 `quantiles[i]` に割り当てられます。

# 例

```
julia> scores1 = rand(10, 2)
julia> quantile_scores1 = get_quantile_scores(scores1)
```
