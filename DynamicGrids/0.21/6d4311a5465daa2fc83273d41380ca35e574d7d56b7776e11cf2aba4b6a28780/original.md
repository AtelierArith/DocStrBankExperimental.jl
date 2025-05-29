```
Rulseset <: AbstractRuleset

Ruleset(rules...; kw...)
Ruleset(rules, settings)
```

A container for holding a sequence of `Rule`s and simulation details like boundary handing and optimisation. Rules will be run in the order they are passed, ie. `Ruleset(rule1, rule2, rule3)`.

# Keywords

  * `proc`: a [`Processor`](@ref) to specificy the hardware to run simulations on,    like [`SingleCPU`](@ref), [`ThreadedCPU`](@ref) or [`CuGPU`](@ref) when    KernelAbstractions.jl and a CUDA gpu is available.
  * `opt`: a [`PerformanceOpt`](@ref) to specificy optimisations like   [`SparseOpt`](@ref). Defaults to [`NoOpt`](@ref).
  * `boundary`: what to do with boundary of grid edges.   Options are `Remove()` or `Wrap()`, defaulting to [`Remove`](@ref).
  * `cellsize`: size of cells.
  * `timestep`: fixed timestep where this is required for some rules.    eg. `Month(1)` or `1u"s"`.
