```
unsafe_backend(model::GenericModel)
```

Return the innermost optimizer associated with the JuMP model `model`.

**This function should only be used by advanced users looking to access low-level solver-specific functionality. It has a high-risk of incorrect usage. We strongly suggest you use the alternative suggested below.**

See also: [`backend`](@ref).

To obtain the index of a variable or constraint in the unsafe backend, use [`optimizer_index`](@ref).

## Unsafe behavior

This function is unsafe for two main reasons.

First, the formulation and order of variables and constraints in the unsafe backend may be different to the variables and constraints in `model`. This can happen because of bridges, or because the solver requires the variables or constraints in a specific order. In addition, the variable or constraint index returned by [`index`](@ref) at the JuMP level may be different to the index of the corresponding variable or constraint in the `unsafe_backend`. There is no solution to this. Use the alternative suggested below instead.

Second, the `unsafe_backend` may be empty, or lack some modifications made to the JuMP model. Thus, before calling `unsafe_backend` you should first call [`MOI.Utilities.attach_optimizer`](@ref) to ensure that the backend is synchronized with the JuMP model.

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer)
A JuMP Model
├ solver: HiGHS
├ objective_sense: FEASIBILITY_SENSE
├ num_variables: 0
├ num_constraints: 0
└ Names registered in the model: none

julia> MOI.Utilities.attach_optimizer(model)

julia> inner = unsafe_backend(model)
A HiGHS model with 0 columns and 0 rows.
```

Moreover, if you modify the JuMP model, the reference you have to the backend (that is, `inner` in the example above) may be out-dated, and you should call [`MOI.Utilities.attach_optimizer`](@ref) again.

This function is also unsafe in the reverse direction: if you modify the unsafe backend, for example, by adding a new constraint to `inner`, the changes may be silently discarded by JuMP when the JuMP `model` is modified or solved.

## Alternative

Instead of `unsafe_backend`, create a model using [`direct_model`](@ref) and call [`backend`](@ref) instead.

For example, instead of:

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, x >= 0)
x

julia> MOI.Utilities.attach_optimizer(model)

julia> highs = unsafe_backend(model)
A HiGHS model with 1 columns and 0 rows.

julia> optimizer_index(x)
MOI.VariableIndex(1)
```

Use:

```jldoctest
julia> import HiGHS

julia> model = direct_model(HiGHS.Optimizer());

julia> set_silent(model)

julia> @variable(model, x >= 0)
x

julia> highs = backend(model)  # No need to call `attach_optimizer`.
A HiGHS model with 1 columns and 0 rows.

julia> index(x)
MOI.VariableIndex(1)
```
