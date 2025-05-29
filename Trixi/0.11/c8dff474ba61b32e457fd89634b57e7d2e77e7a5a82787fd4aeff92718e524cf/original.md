```
VolumeIntegralWeakForm()
```

The classical weak form volume integral type for DG methods as explained in standard textbooks.

## References

  * Kopriva (2009) Implementing Spectral Methods for Partial Differential Equations: Algorithms for Scientists and Engineers [doi: 10.1007/978-90-481-2261-5](https://doi.org/10.1007/978-90-481-2261-5)
  * Hesthaven, Warburton (2007) Nodal Discontinuous Galerkin Methods: Algorithms, Analysis, and Applications [doi: 10.1007/978-0-387-72067-8](https://doi.org/10.1007/978-0-387-72067-8)

`VolumeIntegralWeakForm()` is only implemented for conserved terms as non-conservative terms should always be discretized in conjunction with a flux-splitting scheme, see [`VolumeIntegralFluxDifferencing`](@ref). This treatment is required to achieve, e.g., entropy-stability or well-balancedness.
