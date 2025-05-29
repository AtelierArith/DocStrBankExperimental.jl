```julia
get_normal_form(
    prob,
    br,
    id_bif;
    nev,
    verbose,
    lens,
    Teigvec,
    scaleζ,
    detailed,
    autodiff,
    ζs,
    ζs_ad,
    bls,
    bls_adjoint,
    bls_block
)

```

Compute the normal form of the bifurcation point located at `br.specialpoint[ind_bif]`.

# Arguments

  * `prob::AbstractBifurcationProblem`
  * `br` result from a call to [`continuation`](@ref)
  * `ind_bif` index of the bifurcation point in `br.specialpoint`

# Optional arguments

  * `nev` number of eigenvalues used to compute the spectral projection. This number has to be adjusted when used with iterative methods.
  * `verbose` whether to display information
  * `ζs` list of vectors spanning the kernel of `dF` at the bifurcation point. Useful to enforce the basis for the normal form.
  * `lens::Lens` specify which parameter to take the partial derivative ∂pF
  * `scaleζ` function to normalise the kernel basis. Indeed, when used with large vectors and `norm`, it results in ζs and the normal form coefficient being super small.
  * `autodiff = true` whether to use ForwardDiff for the differentiations w.r.t the parameters that are required to compute the normal form. Used for example for Bogdanov-Takens point. You can set to `autodiff = false` if you wish.
  * `detailed = true` whether to compute only a simplified normal form. Used for example for Bogdanov-Takens point.
  * `bls = MatrixBLS()` specify Bordered linear solver. Used for example for Bogdanov-Takens point.
  * `bls_adjoint = bls` specify Bordered linear solver for the adjoint problem.
  * `bls_block = bls` specify Bordered linear solver when the border has dimension 2 (1 for `bls`).

# Available method

You can directly call 

```
get_normal_form(br, ind_bif ; kwargs...)
```

which is a shortcut for `get_normal_form(getprob(br), br, ind_bif ; kwargs...)`.

Once the normal form `nf` has been computed, you can call `predictor(nf, δp)` to obtain an estimate of the bifurcating branch.
