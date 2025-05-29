```
boundary_condition_slip_wall(u_inner, normal_direction, x, t, surface_flux_function,
                             equations::AcousticPerturbationEquations2D)
```

Use an orthogonal projection of the perturbed velocities to zero out the normal velocity while retaining the possibility of a tangential velocity in the boundary state. Further details are available in the paper:

  * Marcus Bauer, Jürgen Dierke and Roland Ewert (2011) Application of a discontinuous Galerkin method to discretize acoustic perturbation equations [DOI: 10.2514/1.J050333](https://doi.org/10.2514/1.J050333)
