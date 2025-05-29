```
pvalue(x::FisherExactTest; tail = :both, method = :central)
```

Compute the p-value for a given Fisher exact test.

The one-sided p-values are based on Fisher's non-central hypergeometric distribution $f_ω(i)$ with odds ratio $ω$:

$$
    \begin{align*}
        p_ω^{(\text{left})} &=\sum_{i ≤ a} f_ω(i)\\
        p_ω^{(\text{right})} &=\sum_{i ≥ a} f_ω(i)
    \end{align*}
$$

For `tail = :both`, possible values for `method` are:

  * `:central` (default): Central interval, i.e. the p-value is two times the minimum of the one-sided p-values.
  * `:minlike`: Minimum likelihood interval, i.e. the p-value is computed by summing all tables with the same marginals that are equally or less probable:

    $$
        p_ω = \sum_{f_ω(i)≤ f_ω(a)} f_ω(i)
    $$

# References

  * Gibbons, J.D., Pratt, J.W., P-values: Interpretation and Methodology, American Statistican, 29(1):20-25, 1975.
  * Fay, M.P., Supplementary material to "Confidence intervals that match Fisher’s exact or Blaker’s exact tests". Biostatistics, Volume 11, Issue 2, 1 April 2010, Pages 373–374, [link](https://doi.org/10.1093/biostatistics/kxp050)
