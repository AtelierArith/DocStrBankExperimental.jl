```julia
get_shape(comp::Component{<:Any}) -> ::SVGShape{<:Any}
---
`comp`の`SVGShape`を取得します。これは単にコンポーネントの
型パラメータです。`SVGShape`は`set_shape`との変換を提供するために使用されます。
```

example firstshape::Component{:rect} = rect("sample", x = 5, y = 5, ) second*shape::Component{:star} = star("secondsample", x = 20, y = 10) shape::SVGShape{:star} = get*shape(second_shape)

set*shape(firstshape, shape) get*position(firstshape) (5, 5)

println(get_shape(firstshape)) SVGShape{:star}

# or

set_shape(firstshape, :rect) ```

  * `set_shape`, `SVGShape`, `get_shape`, `ToolipsSVG`, `size(::Component{<:Any})`
