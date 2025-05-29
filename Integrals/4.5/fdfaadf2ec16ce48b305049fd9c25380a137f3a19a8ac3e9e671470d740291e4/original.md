```
QuadGKJL(; order = 7, norm = norm, buffer = nothing)
```

One-dimensional Gauss-Kronrod integration from QuadGK.jl. This method also takes the optional arguments `order` and `norm`. Which are the order of the integration rule and the norm for calculating the error, respectively. Lastly, the `buffer` keyword, if set (e.g. `buffer=true`), will allocate a buffer to reuse for multiple integrals and may require evaluating the integrand unless an `integrand_prototype` is provided. Unlike the `segbuf` keyword to `quadgk`, you do not allocate the buffer as this is handled automatically.

## References

```tex
@article{laurie1997calculation,
title={Calculation of Gauss-Kronrod quadrature rules},
author={Laurie, Dirk},
journal={Mathematics of Computation},
volume={66},
number={219},
pages={1133--1145},
year={1997}
}
```
