```julia
get_shape(comp::Component{<:Any}) -> ::SVGShape{<:Any}
---
Retrieves the `SVGShape` of `comp`, which is simply the component's 
type parameter. `SVGShape` is used to provide conversions with `set_shape`.
```

example firstshape::Component{:rect} = rect("sample", x = 5, y = 5, ) second*shape::Component{:star} = star("secondsample", x = 20, y = 10) shape::SVGShape{:star} = get*shape(second_shape)

set*shape(firstshape, shape) get*position(firstshape) (5, 5)

println(get_shape(firstshape)) SVGShape{:star}

# or

set_shape(firstshape, :rect) ```

  * `set_shape`, `SVGShape`, `get_shape`, `ToolipsSVG`, `size(::Component{<:Any})`
