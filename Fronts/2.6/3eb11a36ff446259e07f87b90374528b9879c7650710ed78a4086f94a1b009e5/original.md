```
diffusivity(prob::InverseProblem) -> Function
```

Extract a diffusivity function `D` from a solution to a semi-infinite one-dimensional nonlinear diffusion problem, where the solution is given as a set of discrete points.

Interpolates the given solution with a PCHIP monotonic spline and uses the Bruce and Klute method to reconstruct `D`.

Due to the method used for interpolation, `D` will be continuous but will have discontinuous derivatives.

# Arguments

  * `prob::InverseProblem`: inverse problem. See [`InverseProblem`](@ref).

# References

GERLERO, G. S.; BERLI, C. L. A.; KLER, P. A. Open-source high-performance software packages for direct and inverse solving of horizontal capillary flow. Capillarity, 2023, vol. 6, no. 2, p. 31-40.

BRUCE, R. R.; KLUTE, A. The measurement of soil moisture diffusivity. Soil Science Society of America Journal, 1956, vol. 20, no. 4, p. 458-462.
