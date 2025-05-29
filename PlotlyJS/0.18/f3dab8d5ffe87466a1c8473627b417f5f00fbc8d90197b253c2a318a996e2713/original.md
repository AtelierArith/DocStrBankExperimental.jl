```
savefig(
    p::Plot, fn::AbstractString;
    format::Union{Nothing,String}=nothing,
    width::Union{Nothing,Int}=nothing,
    height::Union{Nothing,Int}=nothing,
    scale::Union{Nothing,Real}=nothing,
)
```

Save a plot `p` to a file named `fn`. If `format` is given and is one of png, jpeg, webp, svg, pdf, eps, json, or html; it will be the format of the file. By default the format is guessed from the extension of `fn`. `scale` sets the image scale. `width` and `height` set the dimensions, in pixels. Defaults are taken from `p.layout`, or supplied by plotly
