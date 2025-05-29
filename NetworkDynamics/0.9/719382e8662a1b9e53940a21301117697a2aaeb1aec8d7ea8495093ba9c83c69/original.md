```
EdgeModel(; kwargs...)
```

Build a `EdgeModel` according to the keyword arguments.

Main Arguments:

  * `f=nothing`: Dynamic function of the component. Can be nothing if `dim` is 0.
  * `g`: Output function of the component. Usefull helpers: [`AntiSymmetric`](@ref), [`Symmetric`](@ref), [`Fiducial`](@ref), [`Directed`](@ref) and [`StateMask`](@ref).
  * `sym`/`dim`: Symbolic names of the states. If `dim` is provided, `sym` is set automaticially.
  * `outsym`/`outdim`:  Symbolic names of the outputs. If `outdim` is provided, `outsym` is set automaticially.  In general, outsym for edges isa named tuple `(; src, dst)`. However, depending on the `g` function,  it might be enough to provide a single vector or even nothing (e.g. `AntiSymmetric(StateMask(1:2))`).  See [Building `EdgeModel`s](@ref) for examples.
  * psym`/`pdim=0`: Symbolic names of the parameters. If`pdim`is provided,`psym` is set automaticially.
  * `mass_matrix=I`: Mass matrix of component. Can be a vector `v` and is then interpreted as `Diagonal(v)`.
  * `name=dim>0 ? :EdgeM : :StaticEdgeM`: Name of the component.

Optional Arguments:

  * `insym`/`indim`: Symbolic names of the inputs. If `indim` is provided, `insym` is set automaticially.  For edges, `insym` is a named tuple `(; src, dst)`. If give as vector tuple is created automaticially.
  * `src`/`dst`: Index or name of the vertices at src and dst end. Enables graphless constructor.
  * `ff`: `FeedForwardType` of component. Will be typically infered from `g` automaticially.
  * `obssym`/`obsf`: Define additional "observable" states.
  * `symmetadata`/`metadata`: Provide prefilled metadata dictionaries.
  * `extin=nothing`:  Define "external" inputs for the model with Network indices, i.e. `extin=[VIndex(7,:x), ..]`.  Those inputs will be provided as another input vector `f(x, insrc, indst, extin, p, t)` and `g(ysrc, ydst, x, insrc, indst, extin, p, t)`.

All Symbol arguments can be used to set default values, i.e. `psym=[:K=>1, :p]`.
