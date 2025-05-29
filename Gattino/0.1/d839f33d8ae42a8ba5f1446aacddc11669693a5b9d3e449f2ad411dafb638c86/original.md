```julia
set!(ecomp::Pair{Int64, <:ToolipsSVG.ToolipsServables.Servable}, args ...; keyargs ...)
```

`set!` is used in tandem with `open_layer!` to set the properties of elements – usually according to data.

```julia
# sets every component's property statically:
set!(ecomp::Pair{Int64, <:ToolipsSVG.ToolipsServables.Servable}, prop::Symbol, value::Any)
# scales the value based on `vec`, using `max` for values that are `100`-percent of the maximum of `vec`.
set!(ecomp::Pair{Int64, <:ToolipsSVG.ToolipsServables.Servable}, prop::Symbol, vec::Vector{<:Number}; max::Int64 = 10)
# sets value to 
set!(ecomp::Pair{Int64, <:ToolipsSVG.ToolipsServables.Servable}, prop::Symbol, vec::Vector{<:AbstractString})
```

The same dispatches are also available for `style!`.

  * See also: `style!`, `set_gradient!`, `open_layer!`, `set_shape!`, `Context`

```example

```
