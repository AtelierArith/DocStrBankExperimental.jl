```julia
hopf_normal_form(
    prob,
    br,
    ind_hopf;
    nev,
    verbose,
    lens,
    Teigvec,
    detailed,
    autodiff,
    scaleζ
)

```

Compute the Hopf normal form.

# Arguments

  * `prob::AbstractBifurcationProblem` bifurcation problem
  * `br` branch result from a call to [`continuation`](@ref)
  * `ind_hopf` index of the bifurcation point in `br`
  * `options` options for the Newton solver

# Optional arguments

  * `nev = 5` number of eigenvalues to compute to estimate the spectral projector
  * `verbose` bool to print information
  * `lens` parameter axis
  * `detailed = true` compute a simplified normal form or not
  * `Teigvec` vector type of the eigenvectors
  * `scaleζ = norm` norm to normalise the eigenvectors

# Available method

Once the normal form `hopfnf` has been computed, you can call `predictor(hopfnf, ds)` to obtain an estimate of the bifurcating periodic orbit.
