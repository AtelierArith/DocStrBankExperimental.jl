```julia
continuation(br, ind_bif; ...)
continuation(
    br,
    ind_bif,
    options_cont;
    alg,
    δp,
    ampfactor,
    use_normal_form,
    nev,
    usedeflation,
    verbosedeflation,
    max_iter_deflation,
    perturb,
    plot_solution,
    Teigvec,
    scaleζ,
    autodiff,
    tol_fold,
    kwargs_deflated_newton,
    kwargs...
)

```

Automatic branch switching at branch points based on a computation of the normal form. More information is provided in [Branch switching](@ref Branch-switching-page). An example of use is provided in [2d generalized Bratu–Gelfand problem](@ref).

# Arguments

  * `br` branch result from a call to [`continuation`](@ref)
  * `ind_bif` index of the bifurcation point in `br` from which you want to branch from
  * `options_cont` options for the call to [`continuation`](@ref)

# Optional arguments

  * `alg = br.alg` continuation algorithm to be used, default value: `br.alg`
  * `δp` used to specify a specific value for the parameter on the bifurcated branch which is otherwise determined by `options_cont.ds`. This allows to use a step larger than `options_cont.dsmax`.
  * `ampfactor = 1` factor to alter the amplitude of the bifurcated solution. Useful to magnify the bifurcated solution when the bifurcated branch is very steep. Can also be used to select the upper/lower branch in Pitchfork bifurcations. See also `use_normal_form` below.
  * `use_normal_form = true`. If `use_normal_form = true`, the normal form is computed as well as its predictor and a guess is automatically formed. If `use_normal_form = false`, the parameter value `p = p₀ + δp` and the guess `x = x₀ + ampfactor .* e` (where `e` is a vector of the kernel) are used as initial guess. This is useful in case automatic branch switching does not work.
  * `nev` number of eigenvalues to be computed to get the right eigenvector
  * `usedeflation = false` whether to use nonlinear deflation (see [Deflated problems](@ref Deflated-problems)) to help finding the guess on the bifurcated
  * `verbosedeflation` print deflated newton iterations
  * `max_iter_deflation` number of newton steps in deflated newton
  * `perturb = identity` which perturbation function to use during deflated newton
  * `Teigvec = _getvectortype(br)` type of the eigenvector. Useful when `br` was loaded from a file and this information was lost
  * `scaleζ = norm` pass a norm to normalize vectors during normal form computation
  * `plot_solution` change plot solution method in the problem `br.prob`
  * `kwargs` optional arguments to be passed to [`continuation`](@ref), the regular `continuation` one and to [`get_normal_form`](@ref).

!!! tip "Advanced use"
    In the case of a very large model and use of special hardware (GPU, cluster), we suggest to discouple the computation of the reduced equation, the predictor and the bifurcated branches. Have a look at `methods(BifurcationKit.multicontinuation)` to see how to call these versions. These methods has been tested on GPU with very high memory pressure.

