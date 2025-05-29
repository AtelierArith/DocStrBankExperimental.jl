```julia
continuation(
    br,
    ind_bif,
    _contParams;
    alg,
    δp,
    ampfactor,
    usedeflation,
    linear_algo,
    detailed,
    prm,
    use_normal_form,
    autodiff_nf,
    kwargs...
)

```

Branch switching at a bifurcation point on a branch of periodic orbits (PO) specified by a `br::AbstractBranchResult`. The functional for computing the PO is `br.prob`. A deflated Newton-Krylov solver can be used to improve the branch switching capabilities.

!!! note "deep copy"
    We deepcopy the underlying periodic orbit functional to prevent mutation


# Arguments

  * `br` branch of periodic orbits computed with a [`PeriodicOrbitTrapProblem`](@ref)
  * `ind_bif` index of the branch point
  * `_contParams` continuation parameters, see [`continuation`](@ref)

# Optional arguments

  * `δp = _contParams.ds` used to specify a particular guess for the parameter in the branch which is otherwise determined by `contParams.ds`. This allows to use a step larger than `contParams.dsmax`.
  * `ampfactor = 1` factor which alters the amplitude of the bifurcated solution. Useful to magnify the bifurcated solution when the bifurcated branch is very steep.
  * `usedeflation = true` whether to use nonlinear deflation (see [Deflated problems](@ref)) to help finding the guess on the bifurcated branch

## For normal form

  * `detailed = false` whether to fully compute the normal form.
  * `record_from_solution = (u, p) -> u[end]`, record method used in the bifurcation diagram, by default this records the period of the periodic orbit.
  * `autodiff_nf = true` whether to use `autodiff` in `get_normal_form`. This can be used in case automatic differentiation is not working as intented.

## For continuation

  * `linear_algo = BorderingBLS()`, same as for [`continuation`](@ref)
  * `kwargs` keywords arguments used for a call to the regular [`continuation`](@ref) and the ones specific to periodic orbits (POs).
