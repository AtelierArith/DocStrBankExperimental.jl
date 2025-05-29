```
savefig(
    io::IO,
    p::Plot;
    width::Union{Nothing,Int}=nothing,
    height::Union{Nothing,Int}=nothing,
    scale::Union{Nothing,Real}=nothing,
    format::String="png"
)
```

Save a plot `p` to the io stream `io`. They keyword argument `format` determines the type of data written to the figure and must be one of png, jpeg, webp, svg, pdf, eps, json, or html. `scale` sets the image scale. `width` and `height` set the dimensions, in pixels. Defaults are taken from `p.layout`, or supplied by plotly
