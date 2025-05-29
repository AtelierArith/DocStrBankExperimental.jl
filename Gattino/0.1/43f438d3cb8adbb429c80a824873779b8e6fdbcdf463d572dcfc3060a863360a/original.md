###### gattino layer styling

```julia
style!(ecomp::Pair{Int64, <:ToolipsSVG.ToolipsServables.AbstractComponent}, args ...) -> ::Nothing
```

`style!` has bindings for styling layer data according to data, or otherwise. components.

```julia
# style the value of `stylep` based on the values of `vec` on the open components.
style!(ecomp::Pair{Int64, <:ToolipsSVG.ToolipsServables.AbstractComponent}, vec::Vector{<:Number}, stylep::Pair{String, Int64} ...)
# style each subsequent component with each subsequent element in `vec`
style!(ecomp::Pair{Int64, <:ToolipsSVG.ToolipsServables.AbstractComponent}, key::String, vec::Vector{String})
# regular styling:
style!(ecomp::Pair{Int64, <:ToolipsSVG.ToolipsServables.AbstractComponent}, p::Pair{String, String} ...)
```

note that you can also `style!` by layer `name` on a `Context`.

  * See also: `animate!(::AbstractContext, ::String, ::ToolipsSVG.KeyFrames)`, `set!`, `Context`, `layers`, `open_layer!`

```example

```
