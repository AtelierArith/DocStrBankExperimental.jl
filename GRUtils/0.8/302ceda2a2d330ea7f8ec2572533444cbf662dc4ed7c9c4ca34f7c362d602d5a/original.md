```
geometrykinds([p])
```

Return a list with symbols that represent the kind of the geometries included in the given plot or figure `p`.

If no argument is given, it takes the current plot of the current figure.

# Examples

```julia
julia> # Plot a set of points at values `(x, y)`
julia> # and a regression line passing through `(x, ŷ)`
julia> scatter(x, y)
julia> plot(x, ŷ)
julia> geometrykinds()
2-element Array{Symbol,1}:
 :scatter
 :line
```
