```
ParticleMeshCoupling1D( mesh, no_particles, spline_degree, 
                      smoothing_type )
```

Kernel smoother with splines of arbitrary degree placed on a uniform mesh. Spline with index i starts at point i

  * `delta_x` : Value of grid spacing along both directions.
  * `n_grid` : Array containing number ofpoints along each direction
  * `no_particles` : Number of particles of underlying PIC method
  * `spline_degree` : Degree of smoothing kernel spline
  * `n_span` : Number of intervals where spline non zero (spline_degree + 1)
  * `scaling` : Scaling factor depending on whether :galerkin or :collocation
  * `n_quad_points` : Number of quadrature points
  * `spline_val`: scratch data for spline evaluation
  * `spline_val_more` : more scratch data for spline evaluation
  * `quad_x, quad_w` : quadrature weights and points

!!! note
    Only 1D version is implemented for now

