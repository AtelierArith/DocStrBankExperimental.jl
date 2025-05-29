```julia
continuation(
    br,
    ind_bif,
    _contParams,
    pbPO;
    bif_prob,
    alg,
    δp,
    ampfactor,
    usedeflation,
    detailed,
    use_normal_form,
    autodiff_nf,
    nev,
    kwargs...
)

```

Perform automatic branch switching from a Hopf bifurcation point labelled `ind_bif` in the list of the bifurcated points of a previously computed branch `br::ContResult`. It first computes a Hopf normal form.

# Arguments

  * `br` branch result from a call to `continuation`
  * `ind_hopf` index of the bifurcation point in `br`
  * `contParams` parameters for the call to `continuation`
  * `probPO` problem used to specify the way toc compute the periodic orbit. It can be [`PeriodicOrbitTrapProblem`](@ref), [`PeriodicOrbitOCollProblem`](@ref), [`ShootingProblem`](@ref) or [`PoincareShootingProblem`](@ref) .

# Optional arguments

  * `alg = br.alg` continuation algorithm
  * `δp` used to specify the guess for the parameter on the bifurcated branch which otherwise defaults to `contParams.ds`. This allows to use an initial step larger than `contParams.dsmax`.
  * `ampfactor = 1` multiplicative factor to alter the amplitude of the bifurcated solution. Useful to magnify the bifurcated solution when the bifurcated branch is very steep.
  * `use_normal_form = true` whether to use the normal form in order to compute the predictor. When `false`, `ampfactor` and `δp` are used to make a predictor based on the bifurcating eigenvector. Setting `use_normal_form = false` can be useful when computing the normal form is not possible for example when higher order derivatives are not available.
  * `usedeflation = true` whether to use nonlinear deflation (see [Deflated problems](@ref)) to help finding the guess on the bifurcated branch
  * `nev` number of eigenvalues to be computed to get the right eigenvector
  * `autodiff_nf = true` whether to use `autodiff` in `get_normal_form`. This can be used in case automatic differentiation is not working as intented.
  * all `kwargs` from [`continuation`](@ref)

A modified version of `prob` is passed to `plot_solution` and `finalise_solution`.

!!! note "Linear solver"
    You have to be careful about the options `contParams.newton_options.linsolver`. In the case of Matrix-Free solver, you have to pass the right number of unknowns `N * M + 1`. Note that the options for the preconditioner are not accessible yet.

