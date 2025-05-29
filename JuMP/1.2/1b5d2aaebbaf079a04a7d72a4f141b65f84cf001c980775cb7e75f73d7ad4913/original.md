```
optimize!(
    model::Model;
    ignore_optimize_hook = (model.optimize_hook === nothing),
    _differentiation_backend::MOI.Nonlinear.AbstractAutomaticDifferentiation =
        MOI.Nonlinear.SparseReverseMode(),
    kwargs...,
)
```

Optimize the model.

If an optimizer has not been set yet (see [`set_optimizer`](@ref)), a [`NoOptimizer`](@ref) error is thrown.

If `ignore_optimize_hook == true`, the optimize hook is ignored and the model is solved as if the hook was not set. Keyword arguments `kwargs` are passed to the `optimize_hook`. An error is thrown if `optimize_hook` is `nothing` and keyword arguments are provided.

## Experimental features

These features may change or be removed in any future version of JuMP.

Pass `_differentiation_backend` to set the [`MOI.Nonlinear.AbstractAutomaticDifferentiation`](@ref) backend used to compute derivatives of nonlinear programs.

If you require only `:ExprGraph`, it is more efficient to pass `_differentiation_backend = MOI.Nonlinear.ExprGraphOnly()`.
