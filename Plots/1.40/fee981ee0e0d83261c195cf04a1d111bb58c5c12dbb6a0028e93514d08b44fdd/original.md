```
heatmap(x,y,z)
heatmap!(x,y,z)
```

Plot a heatmap of the rectangular array `z`.

# Keyword arguments

  * `aspect_ratio::Union{Real, Symbol}`: Plot area is resized so                  that 1 y-unit is the same size as                  `aspect_ratio` x-units. With `:none`, images inherit                  aspect ratio of the plot area. Use `:equal` for                  unit aspect ratio. Aliases: (:aspect*ratios,                  :aspectratio, :aspectratios, :axis*ratio, :axisratio,                  :ratio).

# Example

```julia-repl
julia> heatmap(randn(10,10))
```
