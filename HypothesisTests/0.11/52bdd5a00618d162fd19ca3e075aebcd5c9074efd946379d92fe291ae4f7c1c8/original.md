```
confint(x::FisherExactTest; level::Float64=0.95, tail=:both, method=:central)
```

Compute a confidence interval with coverage `level`. One-sided intervals are based on Fisher's non-central hypergeometric distribution. For `tail = :both`, the only `method` implemented yet is the central interval (`:central`).

!!! note
    Since the p-value is not necessarily unimodal, the corresponding confidence region might not be an interval.


# References

  * Gibbons, J.D, Pratt, J.W. P-values: Interpretation and Methodology, American Statistican, 29(1):20-25, 1975.
  * Fay, M.P., Supplementary material to "Confidence intervals that match Fisher’s exact or Blaker’s exact tests". Biostatistics, Volume 11, Issue 2, 1 April 2010, Pages 373–374, [link](https://doi.org/10.1093/biostatistics/kxp050)
