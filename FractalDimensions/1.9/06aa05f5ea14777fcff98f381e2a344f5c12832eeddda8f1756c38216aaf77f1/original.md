```
takens_best_estimate_dim(X, εmax, metric = Chebyshev(), εmin = 0)
```

Use the "Takens' best estimate" [^Takens1985][^Theiler1988] method for estimating the correlation dimension.

The original formula is

$$
\Delta_C \approx \frac{C(\epsilon_\text{max})}{\int_0^{\epsilon_\text{max}}(C(\epsilon) / \epsilon) \, d\epsilon}
$$

where $C$ is the [`correlationsum`](@ref) and $\epsilon_\text{max}$ is an upper cutoff. Here we use the later expression

$$
\Delta_C \approx - \frac{1}{\eta},\quad \eta = \frac{1}{(N-1)^*}\sum_{[i, j]^*}\log(||X_i - X_j|| / \epsilon_\text{max})
$$

where the sum happens for all $i, j$ so that $i < j$ and $||X_i - X_j|| < \epsilon_\text{max}$. In the above expression, the bias in the original paper has already been corrected, as suggested in [^Borovkova1999].

According to [^Borovkova1999], introducing a lower cutoff `εmin` can make the algorithm more stable (no divergence), this option is given but defaults to zero.

If `X` comes from a delay coordinates embedding of a timseries `x`, a recommended value for $\epsilon_\text{max}$ is `std(x)/4`.

You may also use

```julia
Δ_C, Δu_C, Δl_C = FractalDimensions.takens_best_estimate(args...)
```

to obtain the upper and lower 95% confidence intervals. The intervals are estimated from the log-likelihood function by finding the values of `Δ_C` where the function has fallen by 2 from its maximum, see e.g. [^Barlow] chapter 5.3.

[^Takens1985]: Takens, On the numerical determination of the dimension of an attractor, in: B.H.W. Braaksma, B.L.J.F. Takens (Eds.), Dynamical Systems and Bifurcations, in: Lecture Notes in Mathematics, Springer, Berlin, 1985, pp. 99–106.

[^Theiler1988]: Theiler, [Lacunarity in a best estimator of fractal dimension. Physics Letters A, 133(4–5)](https://doi.org/10.1016/0375-9601(88)91016-X)

[^Borovkova1999]: Borovkova et al., [Consistency of the Takens estimator for the correlation dimension. The Annals of Applied Probability, 9, 05 1999.](https://doi.org/10.1214/aoap/1029962747)

[^Barlow]: Barlow, R., Statistics - A Guide to the Use of Statistical Methods in the Physical Sciences. Vol 29. John Wiley & Sons, 1993
