```
issignificant(x, α, adjust = :none)
```

Return a vector of boolean values indicating if the local statistics are significant or not at the desired threshold $α$.

p-values can be adjusted with the `adjust` parameter using the Bonferroni correction `:bonferroni` or controlling for the False Discovery Rate, `:fdr`
