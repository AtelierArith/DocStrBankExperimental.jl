```
gini(score, target; plotauc = false)
```

Return the `gini = (AUC - 0.5)/0.05 = 2AUC - 1`. AUC is the area under the curve while gini is the ratio of (AUC minus the area of the bottom triangle) vs (Area of upper triangle).

For AUC a random model has AUC = 0.5 but for gini a random model has gini = 0.0

To generate a plot set `plotauc=true`.
