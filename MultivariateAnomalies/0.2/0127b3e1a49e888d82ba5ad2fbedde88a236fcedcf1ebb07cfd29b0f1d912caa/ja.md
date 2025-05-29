```
compute_ensemble(m1_scores, m2_scores[, m3_scores, m4_scores]; ensemble = "mean")
```

与えられた異常スコアの平均（`ensemble = "mean"`）、最小（`ensemble = "min"`）、最大（`ensemble = "max"`）または中央値（`ensemble = "median"`）を計算します。2つから4つのスコア入力配列（`m1_scores, ..., m4_scores`）をサポートします。異なる異常検出アルゴリズムのスコアは、`get_quantile_scores()`を使用することで比較可能である必要があります。

# 例

```
julia> using MultivariateAnomalies
julia> scores1 = rand(10, 2)
julia> scores2 = rand(10, 2)
julia> quantile_scores1 = get_quantile_scores(scores1)
julia> quantile_scores2 = get_quantile_scores(scores2)
julia> compute_ensemble(quantile_scores1, quantile_scores2, ensemble = "max")
```
