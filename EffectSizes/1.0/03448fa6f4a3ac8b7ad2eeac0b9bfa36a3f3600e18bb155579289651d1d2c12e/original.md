```
CohenD(xs, ys[, bootstrap]; [quantile=0.95])
```

Calculate Cohen's $d$ effect size index between two vectors `xs` and `ys`.

A confidence interval for the effect size is calculated at the `quantile` quantile. If `bootstrap` is provided, the confidence interval is calculated by resampling from `xs` and `ys` `bootstrap` times.

$$
    d = \frac{m_A - m_B}{s}
$$

where $m$ is the mean and $s$ is the pooled standard deviation:

$$
    s = \sqrt{\frac{(n_A - 1) s_A^2 + (n_B - 1) s_B^2}{n_A + n_B - 2}}
$$

If $m_A$ > $m_B$, $d$ will be positive and if $m_A$ < $m_B$, $d$ will be negative.

!!! note
    `HedgeG` outperforms `CohenD` when sample sizes are < 20.


# Examples

```julia
xs = randn(100000)
ys = randn(100000) .+ 0.01

using EffectSizes
CohenD(xs, ys)

using HypothesisTests
EqualVarianceTTest(xs, ys)
```
