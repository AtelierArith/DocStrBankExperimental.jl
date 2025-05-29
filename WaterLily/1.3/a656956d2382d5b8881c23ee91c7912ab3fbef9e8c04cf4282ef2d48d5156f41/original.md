```
AutoBody(sdf,map=(x,t)->x; compose=true) <: AbstractBody
```

  * `sdf(x::AbstractVector,t::Real)::Real`: signed distance function
  * `map(x::AbstractVector,t::Real)::AbstractVector`: coordinate mapping function
  * `compose::Bool=true`: Flag for composing `sdf=sdf∘map`

Implicitly define a geometry by its `sdf` and optional coordinate `map`. Note: the `map` is composed automatically if `compose=true`, i.e. `sdf(x,t) = sdf(map(x,t),t)`. Both parameters remain independent otherwise. It can be particularly heplful to set `compose=false` when adding mulitple bodies together to create a more complex one.
