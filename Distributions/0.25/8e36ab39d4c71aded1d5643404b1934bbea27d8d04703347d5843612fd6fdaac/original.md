```
Kumaraswamy(a, b)
```

The *Kumaraswamy distribution* with shape parameters `a > 0` and `b > 0` has probability density function

$$
f(x; a, b) = a b x^{a - 1} (1 - x^a)^{b - 1}, \quad 0 < x < 1
$$

It is related to the [Beta distribution](@ref Beta) by the following identity: if $X \sim \operatorname{Kumaraswamy}(a, b)$ then $X^a \sim \operatorname{Beta}(1, b)$. In particular, if $X \sim \operatorname{Kumaraswamy}(1, 1)$ then $X \sim \operatorname{Uniform}(0, 1)$.

External links

  * [Kumaraswamy distribution on Wikipedia](https://en.wikipedia.org/wiki/Kumaraswamy_distribution)

References

  * Kumaraswamy, P. (1980). A generalized probability density function for double-bounded random processes. Journal of Hydrology. 46(1-2), 79-88.
