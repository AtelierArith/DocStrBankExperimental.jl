```julia
polyshape(name::String, p::Pair{String, <:Any} ...; x::Any = 0, y::Any = 0,
sides::Any = 3, r::Any = 100, angle::Any = 2 * pi / sides, args ...) -> ::Component{:star}
```

Builds a `polyshape` component, which is an `SVGShape` compatible with SVG functions from  `ToolipsSVG`. –-

```example
using ToolipsSVG
newshape::Component{:polyshape} = polyshape("mynewpoly", x = 5, y = 6, sides = 4)
```
