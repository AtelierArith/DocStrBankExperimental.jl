##### contexts

```julia
context -> ::AbstractContext
```

A `Context` is a wrapper for a `Component{:svg}` which can be used with mutating methods to  draw scaled shapes onto an SVG window. Contexts are generally created through methods of this  function, which typically take a `Function` and dimensions for the `context`.

To adjust the scaling of a `Context` from a `Context`, use `group`.

  * `group`

Gattino mutating methods (`Gattino._`) may be used from context components or context plotting,  (`?Gattino.context_components`, `?Gattino.context_plotting`) , or `Toolips` components may be drawn from a `Vector{Servable}` with  `draw!`.

  * `draw!`
  * `Gattino.context_components`
  * `Gattino.context_plotting`

####### layers Contexts have layers, which can be mutated using a mixture `Toolips` syntax, such as  `style!`, and `Gattino` layer editing functions. These include...

  * `open_layer!`
  * `delete_layer!`
  * `rename_layer!`
  * `move_layer!`
  * `reshape(con::AbstractContext, layer::String, into::Symbol; args ...)`
  * `style!(con::AbstractContext, s::String, spairs::Pair{String, String} ...)`
  * `style!(con::AbstractContext, spairs::Pair{String, String} ...)`
  * `animate!(con::AbstractContext, layer::String, anim::ToolipsSVG.ToolipsServables.Animation)`

New layers may be created using grouping.

  * `group!`

####### methods
