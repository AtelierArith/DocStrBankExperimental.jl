```
assignments(x, α, adjust = :none)
```

Return a vector with the categories assigned by the local statistic with a significance threshold $α$.

p-values can be adjusted with the `adjust` parameter using the Bonferroni correction `:bonferroni` or controlling for the False Discovery Rate, `:fdr`
