```
initial_condition_eoc_test_coupled_euler_gravity(x, t, equations::CompressibleEulerEquations1D)
```

One dimensional variant of the setup used for convergence tests of the Euler equations with self-gravity from

  * Michael Schlottke-Lakemper, Andrew R. Winters, Hendrik Ranocha, Gregor J. Gassner (2020) A purely hyperbolic discontinuous Galerkin approach for self-gravitating gas dynamics [arXiv: 2008.10593](https://arxiv.org/abs/2008.10593)

!!! note
    There is no additional source term necessary for the manufactured solution in one spatial dimension. Thus, [`source_terms_eoc_test_coupled_euler_gravity`](@ref) is not present there.

