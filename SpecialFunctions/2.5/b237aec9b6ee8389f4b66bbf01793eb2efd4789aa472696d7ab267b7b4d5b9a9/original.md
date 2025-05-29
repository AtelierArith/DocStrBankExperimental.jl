```
expintx(z)
expintx(ν, z)
```

Computes the scaled exponential integral

$$
\exp(z) \operatorname{E}_\nu(z) = e^z \int_1^\infty \frac{e^{-zt}}{t^\nu} \mathrm{d}t.
$$

If $\nu$ is not specified, $\nu = 1$ is used. Arbitrary complex $\nu$ and $z$ are supported.

See also: [`expint(ν, z)`](@ref SpecialFunctions.expint)
