```
squeeze(N::Int, z::Number)
```

Generate a single-mode [squeeze operator](https://en.wikipedia.org/wiki/Squeeze_operator):

$$
\hat{S}(z)=\exp\left( \frac{1}{2} (z^* \hat{a}^2 - z(\hat{a}^\dagger)^2) \right),
$$

where $\hat{a}$ is the bosonic annihilation operator.
