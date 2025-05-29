```
GlassΔ(treatment, control[, bootstrap]; [quantile=0.95])
```

Calculate Glass's $Δ$ effect size index between two vectors `treatment` and `control`.

A confidence interval for the effect size is calculated at the `quantile` quantile. If `bootstrap` is provided, the confidence interval is calculated by resampling from `xs` and `ys` `bootstrap` times.

$$
    Δ = \frac{m_T - m_C}{s_C}
$$

where $m$ is the mean, $s$ is the standard deviation, $T$ is the treatment group and $C$ is the control group.

If $m_T$ > $m_C$, $Δ$ will be positive and if $m_T$ < $m_C$, $Δ$ will be negative.

!!! note
    `GlassΔ` should be used when the standard deviations between the two groups are very different.

