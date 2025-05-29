```
compute_ensemble(m1_scores, m2_scores[, m3_scores, m4_scores]; ensemble = "mean")
```

compute the mean (`ensemble = "mean"`), minimum (`ensemble = "min"`), maximum (`ensemble = "max"`) or median (`ensemble = "median"`) of the given anomaly scores. Supports between 2 and 4 scores input arrays (`m1_scores, ..., m4_scores`). The scores of the different anomaly detection algorithms should be somehow comparable, e.g., by using `get_quantile_scores()` before.

# Examples

```
julia> using MultivariateAnomalies
julia> scores1 = rand(10, 2)
julia> scores2 = rand(10, 2)
julia> quantile_scores1 = get_quantile_scores(scores1)
julia> quantile_scores2 = get_quantile_scores(scores2)
julia> compute_ensemble(quantile_scores1, quantile_scores2, ensemble = "max")
```
