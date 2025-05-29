```
log(M::Rotations, p, X)
log(M::OrthogonalMatrices, p, X)
log(M::UnitaryMatrices, p, X)
```

Compute the logarithmic map, that is, since the resulting $X$ is represented in the Lie algebra,

$$
\log_p q = \log(p^{\mathrm{H}}q)
$$

which is projected onto the skew symmetric matrices for numerical stability.
