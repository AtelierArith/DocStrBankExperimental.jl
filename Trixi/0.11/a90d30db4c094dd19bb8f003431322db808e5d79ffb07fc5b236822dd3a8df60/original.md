```
flux_hindenlang_gassner(u_ll, u_rr, orientation_or_normal_direction,
                        equations::IdealGlmMhdEquations3D)
```

Entropy conserving and kinetic energy preserving two-point flux of Hindenlang and Gassner (2019), extending [`flux_ranocha`](@ref) to the MHD equations.

## References

  * Florian Hindenlang, Gregor Gassner (2019) A new entropy conservative two-point flux for ideal MHD equations derived from first principles. Presented at HONOM 2019: European workshop on high order numerical methods for evolutionary PDEs, theory and applications
  * Hendrik Ranocha (2018) Generalised Summation-by-Parts Operators and Entropy Stability of Numerical Methods for Hyperbolic Balance Laws [PhD thesis, TU Braunschweig](https://cuvillier.de/en/shop/publications/7743)
  * Hendrik Ranocha (2020) Entropy Conserving and Kinetic Energy Preserving Numerical Methods for the Euler Equations Using Summation-by-Parts Operators [Proceedings of ICOSAHOM 2018](https://doi.org/10.1007/978-3-030-39647-3_42)
