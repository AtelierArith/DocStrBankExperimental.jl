```
LogDensityFunction(
    model::Model,
    varinfo::AbstractVarInfo=VarInfo(model),
    context::AbstractContext=DefaultContext();
    adtype::Union{ADTypes.AbstractADType,Nothing}=nothing
)
```

A struct which contains a model, along with all the information necessary to:

  * calculate its log density at a given point;
  * and if `adtype` is provided, calculate the gradient of the log density at

that point.

At its most basic level, a LogDensityFunction wraps the model together with its the type of varinfo to be used, as well as the evaluation context. These must be known in order to calculate the log density (using [`DynamicPPL.evaluate!!`](@ref)).

If the `adtype` keyword argument is provided, then this struct will also store the adtype along with other information for efficient calculation of the gradient of the log density. Note that preparing a `LogDensityFunction` with an AD type `AutoBackend()` requires the AD backend itself to have been loaded (e.g. with `import Backend`).

`DynamicPPL.LogDensityFunction` implements the LogDensityProblems.jl interface. If `adtype` is nothing, then only `logdensity` is implemented. If `adtype` is a concrete AD backend type, then `logdensity_and_gradient` is also implemented.

# Fields

  * `model`: model used for evaluation
  * `varinfo`: varinfo used for evaluation
  * `context`: context used for evaluation; if `nothing`, `leafcontext(model.context)` will be used when applicable
  * `adtype`: AD type used for evaluation of log density gradient. If `nothing`, no gradient can be calculated
  * `prep`: (internal use only) gradient preparation object for the model

# Examples

```jldoctest
julia> using Distributions

julia> using DynamicPPL: LogDensityFunction, contextualize

julia> @model function demo(x)
           m ~ Normal()
           x ~ Normal(m, 1)
       end
demo (generic function with 2 methods)

julia> model = demo(1.0);

julia> f = LogDensityFunction(model);

julia> # It implements the interface of LogDensityProblems.jl.
       using LogDensityProblems

julia> LogDensityProblems.logdensity(f, [0.0])
-2.3378770664093453

julia> LogDensityProblems.dimension(f)
1

julia> # By default it uses `VarInfo` under the hood, but this is not necessary.
       f = LogDensityFunction(model, SimpleVarInfo(model));

julia> LogDensityProblems.logdensity(f, [0.0])
-2.3378770664093453

julia> # This also respects the context in `model`.
       f_prior = LogDensityFunction(contextualize(model, DynamicPPL.PriorContext()), VarInfo(model));

julia> LogDensityProblems.logdensity(f_prior, [0.0]) == logpdf(Normal(), 0.0)
true

julia> # If we also need to calculate the gradient, we can specify an AD backend.
       import ForwardDiff, ADTypes

julia> f = LogDensityFunction(model, adtype=ADTypes.AutoForwardDiff());

julia> LogDensityProblems.logdensity_and_gradient(f, [0.0])
(-2.3378770664093453, [1.0])
```
