```
Plot2D(elements::Array{<:GraphicElement,1},
       options::Array{Any,1})
```

A container for a list of graphics primitives to draw, together with drawing options

# Examples

```julia-repl
julia> Plot([Path([0 0; 1 1]),Polygon([exp(2*pi*im*k/5) for k=1:5])])
```
