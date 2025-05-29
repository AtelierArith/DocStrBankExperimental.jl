```julia
mutable struct Scope{A, PA, PK, PLT, var"356", var"357", var"358", Symbol, var"359", var"366", Int, var"367", var"368", var"369", var"370"} <: Causal.AbstractSink
```

Constructs a `Scope` with input bus `input`. `buflen` is the length of the internal buffer of `Scope`. `plugin` is the additional data processing tool. `args`,`kwargs` are passed into `plots(args...; kwargs...))`. See (https://github.com/JuliaPlots/Plots.jl) for more information.

!!! warning When initialized, the `plot` of `Scope` is closed. See [`open(sink::Scope)`](@ref) and     [`close(sink::Scope)`](@ref).

# Fields

  * `action::Any`: Action of the component to update data
  * `pltargs::Any`: Plottings arguments
  * `pltkwargs::Any`: Plottings keyword arguments
  * `plt::Any`: Plot object of the component
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
  * `input::Any`
  * `buflen::Any`
  * `plugin::Any`
  * `timebuf::Any`
  * `databuf::Any`
  * `sinkcallback::Any`
