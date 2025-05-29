```
backend(model::Model)
```

Return the lower-level MathOptInterface model that sits underneath JuMP. This model depends on which operating mode JuMP is in (see [`mode`](@ref)).

  * If JuMP is in `DIRECT` mode (i.e., the model was created using [`direct_model`](@ref)), the backend will be the optimizer passed to [`direct_model`](@ref).
  * If JuMP is in `MANUAL` or `AUTOMATIC` mode, the backend is a `MOI.Utilities.CachingOptimizer`.

**This function should only be used by advanced users looking to access low-level MathOptInterface or solver-specific functionality.**

## Notes

If JuMP is not in `DIRECT` mode, the type returned by `backend` may change between any JuMP releases. Therefore, only use the public API exposed by MathOptInterface, and do not access internal fields. If you require access to the innermost optimizer, see [`unsafe_backend`](@ref). Alternatively, use [`direct_model`](@ref) to create a JuMP model in `DIRECT` mode.

See also: [`unsafe_backend`](@ref).
