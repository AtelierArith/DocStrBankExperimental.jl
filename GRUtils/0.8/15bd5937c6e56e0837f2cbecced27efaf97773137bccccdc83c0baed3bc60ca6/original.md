```
colormap(cmap)
colormap([cmap,] T::Type{<:Integer}[, byteorder::Bool=false])
```

Set or retrieve the values of the current colormap.

Give the identifier `cmap` to set the colormap. This identifier can be the number or a string with the name of any of the [GR built-in colormaps](https://gr-framework.org/colormaps.html).

Give an integer data type `T` to return the set of colors defined in the current colormap, as a vector of hexadecimal color codes. By default those codes represent the word-ordered RGB values in a little-endian system. The optional argument `byteorder` can be set to `true` in order to retrieve the codes as byte-ordered codes.

At least one of the arguments `cmap::Union{Integer, AbstractString}` or `T::Type{<:Integer}` are required. If `cmap` not given, the previous colormap is left as current. If `T` is not given, the function returns `nothing`.

# Examples

```julia
# Create example point data
x = 8 .* rand(100) .- 4
y = 8 .* rand(100) .- 4
z = sin.(x) + cos.(y)
# Use the "hot" colormap
colormap("hot")
contourf(x, y, z)

```
