```
set_optimizer_model(inf_model::InfiniteModel, opt_model::JuMP.Model;
                    inherit_optimizer::Bool = true)
```

Specify the JuMP model that is used to solve `inf_model`. This is intended for internal use and extensions. Note that `opt_model` should contain extension data to allow it to map to `inf_model` in a manner similar to [`TranscriptionModel`](@ref). `inherit_optimizer` indicates whether [`add_infinite_model_optimizer`](@ref) should be invoked on the new optimizer mode to inherit the optimizer constuctor and attributes currently stored in `inf_model`.

**Example**

```julia-repl
julia> set_optimizer_model(model, TranscriptionModel())

julia> optimizer_model(model)
A JuMP Model
Feasibility problem with:
Variables: 0
Model mode: AUTOMATIC
CachingOptimizer state: NO_OPTIMIZER
Solver name: No optimizer attached.
```
