```julia
set_shape!(con::AbstractContext, layer::String, into::Symbol; args ...) -> ::Nothing
```

Sets the shape of each element in `layer` to `into`. This uses the `ToolipsSVG.SVGShape`  interface to reshape components. The available shapes built into this API are...

  * `:square`
  * `:circle`
  * `:polyshape`
  * `:rect`
  * and `:star`

```example
newscatter = scatter([1, 2, 3], [1, 2, 3])
set_shape!(newscatter, "points", :star)
```
