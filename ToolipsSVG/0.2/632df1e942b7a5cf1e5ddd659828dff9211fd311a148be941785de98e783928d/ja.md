```julia
set_size!(comp::Component{<:Any}, w::Any, h::Any) -> ::Any
```

`set_size` は `Component` `comp` のサイズを設定し、複数のディスパッチを使用して複数の SVG 要素タイプの一貫したサイズキーを作成するために使用できます。 –-

```example
using ToolipsSVG
circ = circle("sample", cx = 5, cy = 5, r = 6)
size(circ)
(6, 6)
set_size!(circ, 9, 10)
size(circ)
(9, 10)

newrect = rect("examplerect", x = 50, y = 70, width = 400, height = 200)
set_size!(newrect, size(circ) ...)

size(newrect)
(9, 10)
```

  * 参照: `size`, `star`, `polyshape`, `set_position!`, set_shape
