```
check_model_and_trace([rng, ]model::Model; kwargs...)
```

Check that `model` is valid, warning about any potential issues.

This will check the model for the following issues:

1. Repeated usage of the same varname in a model.
2. Incorrectly treating a variable as random rather than fixed, and vice versa.

# Arguments

  * `rng::Random.AbstractRNG`: The random number generator to use when evaluating the model.
  * `model::Model`: The model to check.

# Keyword Arguments

  * `varinfo::VarInfo`: The varinfo to use when evaluating the model. Default: `VarInfo(model)`.
  * `context::AbstractContext`: The context to use when evaluating the model. Default: [`DefaultContext`](@ref).
  * `error_on_failure::Bool`: Whether to throw an error if the model check fails. Default: `false`.

# Returns

  * `issuccess::Bool`: Whether the model check succeeded.
  * `trace::Vector{Stmt}`: The trace of statements executed during the model check.

# Examples

## Correct model

```jldoctest check-model-and-tracecheck-model-and-trace; setup=:(using Distributions)
julia> using StableRNGs

julia> rng = StableRNG(42);

julia> @model demo_correct() = x ~ Normal()
demo_correct (generic function with 2 methods)

julia> issuccess, trace = check_model_and_trace(rng, demo_correct());

julia> issuccess
true

julia> print(trace)
 assume: x ~ Normal{Float64}(μ=0.0, σ=1.0) ⟼ -0.670252 (logprob = -1.14356)

julia> issuccess, trace = check_model_and_trace(rng, demo_correct() | (x = 1.0,));
┌ Warning: The model does not contain any parameters.
└ @ DynamicPPL.DebugUtils DynamicPPL.jl/src/debug_utils.jl:342

julia> issuccess
true

julia> print(trace)
observe: 1.0 ~ Normal{Float64}(μ=0.0, σ=1.0) (logprob = -1.41894)
```

## Incorrect model

```jldoctest check-model-and-tracecheck-model-and-trace; setup=:(using Distributions)
julia> @model function demo_incorrect()
           # (×) Sampling `x` twice will lead to incorrect log-probabilities!
           x ~ Normal()
           x ~ Exponential()
       end
demo_incorrect (generic function with 2 methods)

julia> issuccess, trace = check_model_and_trace(rng, demo_incorrect(); error_on_failure=true);
ERROR: varname x used multiple times in model
```
