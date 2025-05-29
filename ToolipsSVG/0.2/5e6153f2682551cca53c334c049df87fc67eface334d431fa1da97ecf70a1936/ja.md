```julia
polyshape(name::String, p::Pair{String, <:Any} ...; x::Any = 0, y::Any = 0,
sides::Any = 3, r::Any = 100, angle::Any = 2 * pi / sides, args ...) -> ::Component{:star}
```

`polyshape` コンポーネントを構築します。これは `ToolipsSVG` の SVG 関数と互換性のある `SVGShape` です。 –-

```example
using ToolipsSVG
newshape::Component{:polyshape} = polyshape("mynewpoly", x = 5, y = 6, sides = 4)
```
