```
draw(state[,els];kwargs...)
```

`state` a single `State`. `els` specifies which elements to draw and can be either

  * a vector of `EleID`s (obtained from [`addelement!`](@ref)`), all corresponding to the same concrete element type
  * a concrete element type (see [`eletyp`](@ref)).
  * omitted: all the element of the model are drawn.

`kwargs...` is any additional key words arguments that will be passed to the `draw` method of each element,  for example to specify colors, etc.  See the elements' documentation.

See also: [`getdof`](@ref), [`@request`](@ref), [`@espy`](@ref), [`addelement!`](@ref), [`solve`](@ref)
