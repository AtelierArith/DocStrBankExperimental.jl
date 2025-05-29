Created in December, 2023 by [chifi - an open source software dynasty.](https://github.com/orgs/ChifiSource)

  * This software is MIT-licensed.

### Gattino

`Gattino` is a **hyper-composable** SVG visualization library for Julia built using the `Toolips`  web-development framework's HTML templating (`ToolipsSVG`). Usage centers around the `Context`,  which is provided to translate data into Scalable Vector Graphics and scale it onto a window. A  `Context` is usually created via the `context` function:

```julia
mycon = context(200, 200) do con::Context
    text!(con, 250, 250, "hello world!")
    points!(con, [1, 2, 3, 4], [1, 2, 3, 4])
end
```

`Gattino`

  * For more information on creating and editing visualizations, use `?context`.

###### names

  * **colors** (not exported)

```julia
randcolor
make_gradient
```

  * **visualizations** (exported)

```julia
# plot   | context plotting equivalent
scatter #| scatter_plot!
line    #| line_plot!
hist    #| hist_plot!
```

  * **contexts** (exported)

```julia
AbstractContext
vcat(comp::AbstractContext, cons::AbstractContext ...)
hcat(comp::AbstractContext, cons::AbstractContext ...)
vcat(comp::Component{:div}, cons::AbstractContext ...)
hcat(comp::Component{:div}, cons::AbstractContext ...)
Context
context
layers
draw!
Group
group
group!
style!(con::AbstractContext, s::String, spairs::Pair{String, String} ...)
ToolipsServables.animate!(con::AbstractContext, layer::String, animation::ToolipsSVG.KeyFrames)
merge!(c::AbstractContext, c2::AbstractContext)
delete_layer!
rename_layer!
move_layer!
set_shape!
open_layer!
set!
set_gradient!
style!(ecomp::Pair{Int64, <:ToolipsSVG.ToolipsServables.AbstractComponent}, vec::Vector{<:Number}, stylep::Pair{String, Int64} ...)
compress!
```

  * **context plotting** (not exported)

```julia
text!
line!
gridlabels!
grid!
labeled_grid!
points!
axes!
axislabels!
bars!
barlabels!
v_bars!
v_barlabels!
legend!
append_legend!
make_legend_preview
```
