```
InfiniteModel([optimizer_constructor];
              [OptimizerModel::Function = TranscriptionModel,
              add_bridges::Bool = true, optimizer_model_kwargs...])
```

Return a new infinite model where an optimizer is specified if an `optimizer_constructor` is given. The optimizer can also later be set with the [`JuMP.set_optimizer`](@ref) call. By default the `optimizer_model` data field is initialized with a [`TranscriptionModel`](@ref), but a different type of model can be assigned via [`set_optimizer_model`](@ref) as can be required by extensions.

**Example**

```jldoctest
julia> using InfiniteOpt, JuMP, Ipopt;

julia> model = InfiniteModel()
An InfiniteOpt Model
Feasibility problem with:
Finite Parameters: 0
Infinite Parameters: 0
Variables: 0
Measures: 0
Derivatives: 0
Optimizer model backend information:
Model mode: AUTOMATIC
CachingOptimizer state: NO_OPTIMIZER
Solver name: No optimizer attached.

julia> model = InfiniteModel(Ipopt.Optimizer)
An InfiniteOpt Model
Feasibility problem with:
Finite Parameters: 0
Infinite Parameters: 0
Variables: 0
Measures: 0
Derivatives: 0
Optimizer model backend information:
Model mode: AUTOMATIC
CachingOptimizer state: EMPTY_OPTIMIZER
Solver name: Ipopt
```
