```
confint(test::HypothesisTest; level = 0.95, tail = :both)
```

Compute a confidence interval C with coverage `level`.

If `tail` is `:both` (default), then a two-sided confidence interval is returned. If `tail` is `:left` or `:right`, then a one-sided confidence interval is returned.

!!! note
    Most of the implemented confidence intervals are *strongly consistent*, that is, the confidence interval with coverage `level` does not contain the test statistic under $h_0$ if and only if the corresponding test rejects the null hypothesis $h_0: θ = θ_0$:

    $$
        C (x, level) = \{θ : p_θ (x) > 1 - level\},
    $$

    where $p_θ$ is the [`pvalue`](@ref) of the corresponding test.

