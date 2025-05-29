```
options = ContinuationPar(dsmin = 1e-4,...)
```

Returns a variable containing parameters to affect the `continuation` algorithm used to solve `F(x, p) = 0`.

# Arguments

  * `dsmin, dsmax` are the minimum, maximum arclength allowed value. It controls the density of points in the computed branch of solutions.
  * `ds = 0.01` is the initial arclength.
  * `p_min, p_max` allowed parameter range for `p`
  * `max_steps = 100` maximum number of continuation steps
  * `newton_options::NewtonPar`: options for the Newton algorithm
  * `save_to_file = false`: save to file. A name is automatically generated or can be defined in [`continuation`](@ref). This requires `using JLD2`.
  * `save_sol_every_step::Int64 = 0` at which continuation steps do we save the current solution
  * `plot_every_step = 10` at which continuation steps do we plot the current solution

## Handling eigen elements, their computation is triggered by the argument `detect_bifurcation` (see below)

  * `nev = 3` number of eigenvalues to be computed. It is automatically increased to have at least `nev` unstable eigenvalues. To be set for proper  bifurcation detection. See [Detection of bifurcation points of Equilibria](@ref) for more informations.
  * `save_eig_every_step = 1` record eigen vectors every specified steps. **Important** for memory limited resource, *e.g.* GPU.
  * `save_eigenvectors = true` **Important** for memory limited resource, *e.g.* GPU.

## Handling bifurcation detection

  * `tol_stability = 1e-10` lower bound on the real part of the eigenvalues to test for stability of equilibria and periodic orbits
  * `detect_fold = true` detect Fold bifurcations? It is a useful option although the detection of Fold is cheap. Indeed, it may happen that there is a lot of Fold points and this can saturate the memory in memory limited devices (e.g. on GPU)
  * `detect_bifurcation::Int` ∈ {0, 1, 2, 3} If set to 0, nothing is done. If set to 1, the eigen-elements are computed. If set to 2, the bifurcations points are detected during the continuation run, but not located precisely. If set to 3, a bisection algorithm is used to locate the bifurcations points (slower). The possibility to switch off detection is a useful option. Indeed, it may happen that there are a lot of bifurcation points and this can saturate the memory of memory limited devices (e.g. on GPU)
  * `dsmin_bisection = 1e-16` dsmin for the bisection algorithm for locating bifurcation points
  * `n_inversion = 2` number of sign inversions in bisection algorithm
  * `max_bisection_steps = 15` maximum number of bisection steps
  * `tol_bisection_eigenvalue = 1e-16` tolerance on real part of eigenvalue to detect bifurcation points in the bisection steps

## Handling `ds` adaptation (see [`continuation`](@ref) for more information)

  * `a  = 0.5` aggressiveness factor. It is used to adapt `ds` in order to have a number of newton iterations per continuation step roughly constant. The higher `a` is, the larger the step size `ds` is changed at each continuation step.

## Handling event detection

  * `detect_event::Int` ∈ {0, 1, 2} If set to 0, nothing is done. If set to 1, the event locations are sought during the continuation run, but not located precisely. If set to 2, a bisection algorithm is used to locate the event (slower).
  * `tol_param_bisection_event = 1e-16` tolerance on parameter to locate event

## Misc

  * `η = 150.` parameter to estimate tangent at first point with parameter  p₀ + ds / η
  * `detect_loop` [WORK IN PROGRESS] detect loops in the branch and stop the continuation

!!! tip "Mutating"
    For performance reasons, we decided to use an immutable structure to hold the parameters. One can use the package `Accessors.jl` to drastically simplify the mutation of different fields. See tutorials for more examples.

