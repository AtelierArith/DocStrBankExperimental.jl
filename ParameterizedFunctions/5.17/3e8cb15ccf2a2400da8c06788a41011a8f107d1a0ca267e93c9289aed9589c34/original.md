```julia
ode_def_opts(name::Symbol, opts::Dict{Symbol, Bool}, curmod, ex::Expr, params...;
    depvar = :t)
```

The core internal. Users should only interact with this through the `@ode_def_*` macros.

Options are self-explanatory by name mapping to `ODEFunction`:

  * build_tgrad
  * build_jac
  * build_expjac
  * build_invjac
  * build_invW
  * build*invW*t
  * build_hes
  * build_invhes
  * build_dpfuncs

`depvar` sets the symbol for the dependent variable.

Example:

```julia
opts = Dict{Symbol, Bool}(:build_tgrad => true,
    :build_jac => true,
    :build_expjac => false,
    :build_invjac => true,
    :build_invW => true,
    :build_invW_t => true,
    :build_hes => false,
    :build_invhes => false,
    :build_dpfuncs => true)
```
