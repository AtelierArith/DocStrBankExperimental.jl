```
backend(model::GenericModel)
```

Return the lower-level MathOptInterface model that sits underneath JuMP. This model depends on which operating mode JuMP is in (see [`mode`](@ref)).

  * If JuMP is in `DIRECT` mode (that is, the model was created using [`direct_model`](@ref)), the backend will be the optimizer passed to [`direct_model`](@ref).
  * If JuMP is in `MANUAL` or `AUTOMATIC` mode, the backend is a `MOI.Utilities.CachingOptimizer`.

Use [`index`](@ref) to get the index of a variable or constraint in the backend model.

!!! warning
    This function should only be used by advanced users looking to access low-level MathOptInterface or solver-specific functionality.


## Notes

If JuMP is not in `DIRECT` mode, the type returned by `backend` may change between any JuMP releases. Therefore, only use the public API exposed by MathOptInterface, and do not access internal fields. If you require access to the innermost optimizer, see [`unsafe_backend`](@ref). Alternatively, use [`direct_model`](@ref) to create a JuMP model in `DIRECT` mode.

See also: [`unsafe_backend`](@ref).

## Example

```jldoctest
julia> import HiGHS

julia> model = direct_model(HiGHS.Optimizer());

julia> set_silent(model)

julia> @variable(model, x >= 0)
x

julia> highs = backend(model)
A HiGHS model with 1 columns and 0 rows.

julia> index(x)
MOI.VariableIndex(1)
```
