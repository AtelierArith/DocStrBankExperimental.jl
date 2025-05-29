```
pdfsquaredL2norm(d::Distribution)
```

Return the square of the L2 norm of the probability density function $f(x)$ of the distribution `d`:

$$
\int_{S} f(x)^{2} \mathrm{d} x
$$

where $S$ is the support of $f(x)$.
