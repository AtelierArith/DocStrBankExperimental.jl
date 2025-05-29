```
TranscriptionModel([optimizer_constructor;
                   caching_mode::MOIU.CachingOptimizerMode = MOIU.AUTOMATIC,
                   bridge_constraints::Bool = true])::JuMP.Model
```

Return a `JuMP.Model` with [`TranscriptionData`](@ref) included in the `ext` data field. Accepts the same arguments as a typical JuMP `Model`. More detailed variable and constraint naming can be enabled via `verbose_naming`.

**Example**

```julia-repl
julia> TranscriptionModel()
A JuMP Model
Feasibility problem with:
Variables: 0
Model mode: AUTOMATIC
CachingOptimizer state: NO_OPTIMIZER
Solver name: No optimizer attached.
```
