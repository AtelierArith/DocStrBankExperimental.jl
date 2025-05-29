```
ExtendedBeta
```

The [**extended beta distribution**](https://www.vosesoftware.com/riskwiki/Beta4distribution.php) with shape parameters `α` and `β`, and optional support parameters `min` and `max` has a probability density function

$$
f(x, α, β, \text{min}, \text{max}) =
    \begin{cases}
        0,                                                                                              &\text{if:}~x < \text{min},               \\
        \frac{(x-\text{min})^{α-1} (\text{max}-x)^{β-1}}{B(α,β) (\text{max}-\text{min})^{α+β-1}},  &\text{if:}~\text{min} ≤ x ≤ \text{max}, \\
        0,                                                                                              &\text{if:}~x > max,
    \end{cases}
$$

where B(α,β) is a Beta function.
