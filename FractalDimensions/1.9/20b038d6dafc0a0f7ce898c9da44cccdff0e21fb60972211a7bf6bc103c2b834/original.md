```
estimate_r0_theiler(X::AbstractStateSpaceSet) → r0, ε0
```

Estimate a reasonable size for boxing the data `X` before calculating the [`boxed_correlationsum`](@ref) proposed by [Theiler1987](@cite). Return the boxing size `r0` and minimum inter-point distance in `X`, `ε0`.

To do so the dimension is estimated by running the algorithm by Grassberger and Procaccia [Grassberger1983](@cite) with `√N` points where `N` is the number of total data points. Then the optimal boxsize $r_0$ computes as

$$
r_0 = R (2/N)^{1/\nu}
$$

where $R$ is the size of the chaotic attractor and $\nu$ is the estimated dimension.
