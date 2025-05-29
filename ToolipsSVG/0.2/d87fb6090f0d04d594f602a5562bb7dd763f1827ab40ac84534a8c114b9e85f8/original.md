```julia
get_position(comp::Component{<:Any}) -> ::Tuple{Int64, Int64}
```

Similar to `size(comp::Component{<:Any})`, this `Function` is  used to get the position of many different SVG component types  in the same way. Also like size, position may also be set with  `set_position!`. –-

```example
using ToolipsSVG
rct = rect("samp-rect", x = 5, y = 5, width = 20, height = 10)
get_position(rct)
(5, 5)
```

  * See also: `size(<:ToolipsSVG.ToolipsServables.AbstractComponent)`, `set_size!`, `set_position!`
