```
pvalue(test::SurrogateTest; tail = :left)
```

Return the [p-value](https://en.wikipedia.org/wiki/P-value) corresponding to the given [`SurrogateTest`](@ref), optionally specifying what kind of tail test to do (one of `:left, :right, :both`).

For [`SurrogateTest`](@ref), the p-value is simply the proportion of surrogate statistics that exceed (for `tail = :right`) or subseed (`tail = :left`) the discriminatory statistic computed from the input data.

The default value of `tail` assumes that the surrogate data are expected to have higher discriminatory statistic values. This is the case for statistics that quantify entropy. For statistics that quantify autocorrelation, use `tail = :right` instead.
