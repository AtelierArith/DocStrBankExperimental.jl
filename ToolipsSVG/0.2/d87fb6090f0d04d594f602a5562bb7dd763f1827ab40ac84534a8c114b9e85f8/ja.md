```julia
get_position(comp::Component{<:Any}) -> ::Tuple{Int64, Int64}
```

`size(comp::Component{<:Any})`と同様に、この`Function`は、同じ方法で多くの異なるSVGコンポーネントタイプの位置を取得するために使用されます。サイズと同様に、位置も`set_position!`で設定できます。 –-

```example
using ToolipsSVG
rct = rect("samp-rect", x = 5, y = 5, width = 20, height = 10)
get_position(rct)
(5, 5)
```

  * 参照: `size(<:ToolipsSVG.ToolipsServables.AbstractComponent)`, `set_size!`, `set_position!`
