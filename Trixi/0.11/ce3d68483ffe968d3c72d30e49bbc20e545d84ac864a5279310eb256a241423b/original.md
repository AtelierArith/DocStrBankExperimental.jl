```
source_terms_eoc_test_euler(u, x, t, equations::CompressibleEulerEquations3D)
```

Setup used for convergence tests of the Euler equations with self-gravity used in

  * Michael Schlottke-Lakemper, Andrew R. Winters, Hendrik Ranocha, Gregor J. Gassner (2020) A purely hyperbolic discontinuous Galerkin approach for self-gravitating gas dynamics [arXiv: 2008.10593](https://arxiv.org/abs/2008.10593)

in combination with [`initial_condition_eoc_test_coupled_euler_gravity`](@ref).

!!! note
    This method is to be used for testing pure Euler simulations with analytic self-gravity. If you intend to do coupled Euler-gravity simulations, you need to use [`source_terms_eoc_test_coupled_euler_gravity`](@ref) instead.

