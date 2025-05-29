```
initial_condition_eoc_test_coupled_euler_gravity(x, t, equations::CompressibleEulerEquations2D)
```

Setup used for convergence tests of the Euler equations with self-gravity used in

  * Michael Schlottke-Lakemper, Andrew R. Winters, Hendrik Ranocha, Gregor J. Gassner (2020) A purely hyperbolic discontinuous Galerkin approach for self-gravitating gas dynamics [arXiv: 2008.10593](https://arxiv.org/abs/2008.10593)

in combination with [`source_terms_eoc_test_coupled_euler_gravity`](@ref) or [`source_terms_eoc_test_euler`](@ref).
