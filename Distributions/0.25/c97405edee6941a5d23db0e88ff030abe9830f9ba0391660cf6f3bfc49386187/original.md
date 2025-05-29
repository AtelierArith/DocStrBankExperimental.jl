```
Lindley(θ)
```

The one-parameter *Lindley distribution* with shape `θ > 0` has probability density function

$$
f(x; \theta) = \frac{\theta^2}{1 + \theta} (1 + x) e^{-\theta x}, \quad x > 0
$$

It was first described by Lindley[^1] and was studied in greater detail by Ghitany et al.[^2] Note that `Lindley(θ)` is a mixture of an `Exponential(θ)` and a `Gamma(2, θ)` with respective mixing weights `p = θ/(1 + θ)` and `1 - p`.

[^1]: Lindley, D. V. (1958). Fiducial Distributions and Bayes' Theorem. Journal of the   Royal Statistical Society: Series B (Methodological), 20(1), 102–107.

[^2]: Ghitany, M. E., Atieh, B., & Nadarajah, S. (2008). Lindley distribution and its   application. Mathematics and Computers in Simulation, 78(4), 493–506.
