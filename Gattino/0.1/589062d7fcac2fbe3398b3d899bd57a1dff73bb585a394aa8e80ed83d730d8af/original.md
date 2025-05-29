###### gattino context styling

```julia
style!(con::AbstractContext, args ...) -> ::Nothing
```

`style!` is extended to work with `Gattino` contexts. We can style the window with  `style!(con::AbstractContext, spairs::Pair{String, String} ...)` and style layers with  `style!(con::AbstractContext, s::String, spairs::Pair{String, String} ...)` just as we would normal  components.

```julia
style!(con::AbstractContext, s::String, spairs::Pair{String, String} ...)
style!(con::AbstractContext, spairs::Pair{String, String} ...)
```

  * See also: `animate!(::AbstractContext, ::String, ::ToolipsSVG.KeyFrames)`, `set!`, `Context`, `layers`

```example

```
