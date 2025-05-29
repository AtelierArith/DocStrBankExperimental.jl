```
VertexModel(; kwargs...)
```

Build a `VertexModel` according to the keyword arguments.

Main Arguments:

  * `f=nothing`: Dynamic function of the component. Can be nothing if `dim` is 0.
  * `g`: Output function of the component. Usefull helpers: [`StateMask`](@ref)
  * `sym`/`dim`: Symbolic names of the states. If `dim` is provided, `sym` is set automaticially.
  * `outsym`/`outdim`:  Symbolic names of the outputs. If `outdim` is provided, `outsym` is set automaticially.  Can be infered automaticially if `g` isa `StateMask`.
  * psym`/`pdim=0`: Symbolic names of the parameters. If`pdim`is provided,`psym` is set automaticially.
  * `mass_matrix=I`: Mass matrix of component. Can be a vector `v` and is then interpreted as `Diagonal(v)`.
  * `name=dim>0 ? :VertexM : :StaticVertexM`: Name of the component.

Optional Arguments:

  * `insym`/`indim`: Symbolic names of the inputs. If `indim` is provided, `insym` is set automaticially.
  * `vidx`: Index of the vertex in the graph, enables graphless constructor.
  * `ff`: `FeedForwardType` of component. Will be typically infered from `g` automaticially.
  * `obssym`/`obsf`: Define additional "observable" states.
  * `symmetadata`/`metadata`: Provide prefilled metadata dictionaries.
  * `extin=nothing`:  Define "external" inputs for the model with Network indices, i.e. `extin=[VIndex(7,:x), ..]`.  Those inputs will be provided as another input vector `f(x, in, extin, p, t)` and `g(y, x, in, extin, p, t)`.

All Symbol arguments can be used to set default values, i.e. `psym=[:K=>1, :p]`.
