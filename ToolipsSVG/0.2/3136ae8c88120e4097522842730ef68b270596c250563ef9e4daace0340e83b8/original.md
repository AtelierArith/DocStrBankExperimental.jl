```julia
set_shape(comp::Component{<:Any}, into::Symbol; args ...)
---
`set_shape` is used to turn a shape into another shape with the same 
size and position.

```

example firstshape::Component{:rect} = rect("sample", x = 5, y = 5, ) second*shape::Component{:star} = star("secondsample", x = 20, y = 10) shape::SVGShape{:star} = get*shape(second_shape)

set*shape(firstshape, shape) get*position(firstshape) (5, 5)

println(get_shape(firstshape)) SVGShape{:star}

# or

set_shape(firstshape, :rect) ```
