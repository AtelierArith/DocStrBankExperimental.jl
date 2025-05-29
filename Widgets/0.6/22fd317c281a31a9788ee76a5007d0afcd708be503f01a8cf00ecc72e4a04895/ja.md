`@layout!(d, x)`

`d.layout`を`Widgets.@layout(x)`の結果に合わせて設定します。詳細については[`Widgets.@layout`](@ref)を参照してください。

## 例

```jldoctest map
julia> using Interact

julia> t = Widget{:test}(OrderedDict(:b => slider(1:100), :c => button()));

julia> @layout! t hbox(:b, CSSUtil.hskip(1em), :c);
```
