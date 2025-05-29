```julia
star(name::String, p::Pair{String, <:Any} ...; x::Any = 0, y::Any = 0, points::Any = 5, 
outer_radius::Any = 100, inner_radius::Any = 200, angle::Any = pi / points, args ...) -> ::Component{:star}
```

特別な `SVG` `:star` `Component` を構築します。これは、合成可能な星になるように特別に型付けされた `:polygon` タグ付き要素です。同様に、`ToolipsSVG` も `polyshape` `Component` を提供します。 –-

```example
using ToolipsSVG
newshape::Component{:star} = star("mynewstar", x = 5, y = 6, points = 6)
```
