```
expectile(x̃, α)
```

Compute the expectile risk measure of the random variable `x̃` with risk level `α ∈ (0,1)`. When `α = 1/2`, the function computes the expected value.

```
expectile(values, pmf, α; ...)
```

Compute expectile for a discrete random variable with `values` and the probability mass function `pmf`.

Expectile is only coherent when `α ∈ (0,1/2]

Notice the range for `α` does not include `0` or `1`.

The function solves

$$
\argmin_{x ∈ Real} α \mathbb{E}((x̃ - x)^2_+) - (1-α) \mathbb{E}((x̃ - x)^2_-)
$$
