`@layout!(d, x)`

Set `d.layout` to match the result of `Widgets.@layout(x)`. See [`Widgets.@layout`](@ref) for more information.

## Examples

```jldoctest map
julia> using Interact

julia> t = Widget{:test}(OrderedDict(:b => slider(1:100), :c => button()));

julia> @layout! t hbox(:b, CSSUtil.hskip(1em), :c);
```
