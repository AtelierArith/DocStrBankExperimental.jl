```julia
star(name::String, p::Pair{String, <:Any} ...; x::Any = 0, y::Any = 0, points::Any = 5, 
outer_radius::Any = 100, inner_radius::Any = 200, angle::Any = pi / points, args ...) -> ::Component{:star}
```

Builds a special `SVG` `:star` `Component`. This is a `:polygon` tagged element  that is specially typed in order to become a composable star. Similarly, `ToolipsSVG` also provides the  `polyshape` `Component`. –-

```example
using ToolipsSVG
newshape::Component{:star} = star("mynewstar", x = 5, y = 6, points = 6)
```
