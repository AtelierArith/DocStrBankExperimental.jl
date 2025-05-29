```julia
set_position!(comp::Component{<:Any}, x::Any, y::Any) -> ::Any
```

## `comp`の位置を`x`と`y`に設定します。

```example
newrect = rect("examplerect", x = 50, y = 70, width = 400, height = 200)
get_position(new_rect)
(50, 760)

set_position!(new_rect, (70, 90) ...)
get_position(new_rect)
(70, 90)
```

  * 参照: `get_position`, `get_shape`, `set_shape`, `size(::Component{<:Any})`
