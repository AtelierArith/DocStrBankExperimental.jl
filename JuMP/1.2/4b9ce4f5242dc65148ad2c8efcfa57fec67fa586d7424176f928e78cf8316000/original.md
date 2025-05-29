```
unsafe_backend(model::Model)
```

Return the innermost optimizer associated with the JuMP model `model`.

**This function should only be used by advanced users looking to access low-level solver-specific functionality. It has a high-risk of incorrect usage. We strongly suggest you use the alternative suggested below.**

See also: [`backend`](@ref).

## Unsafe behavior

This function is unsafe for two main reasons.

First, the formulation and order of variables and constraints in the unsafe backend may be different to the variables and constraints in `model`. This can happen because of bridges, or because the solver requires the variables or constraints in a specific order. In addition, the variable or constraint index returned by [`index`](@ref) at the JuMP level may be different to the index of the corresponding variable or constraint in the `unsafe_backend`. There is no solution to this. Use the alternative suggested below instead.

Second, the `unsafe_backend` may be empty, or lack some modifications made to the JuMP model. Thus, before calling `unsafe_backend` you should first call [`MOI.Utilities.attach_optimizer`](@ref) to ensure that the backend is synchronized with the JuMP model.

```julia
MOI.Utilities.attach_optimizer(model)
inner = unsafe_backend(model)
```

Moreover, if you modify the JuMP model, the reference you have to the backend (i.e., `inner` in the example above) may be out-dated, and you should call [`MOI.Utilities.attach_optimizer`](@ref) again.

This function is also unsafe in the reverse direction: if you modify the unsafe backend, e.g., by adding a new constraint to `inner`, the changes may be silently discarded by JuMP when the JuMP `model` is modified or solved.

## Alternative

Instead of `unsafe_backend`, create a model using [`direct_model`](@ref) and call [`backend`](@ref) instead.

For example, instead of:

```julia
model = Model(HiGHS.Optimizer)
@variable(model, x >= 0)
MOI.Utilities.attach_optimizer(model)
highs = unsafe_backend(model)
```

Use:

```julia
model = direct_model(HiGHS.Optimizer())
@variable(model, x >= 0)
highs = backend(model)  # No need to call `attach_optimizer`.
```
