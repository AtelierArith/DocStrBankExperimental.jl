```
PixelMap(pixels, lowerleft, upperright; kwargs...)
```

A graphics primitive representing a two-dimensional array of pixels situated in the box with given lower left and upper  right corners.

`pixels` is an array of `NamedColor`s, while `lowerleft`  and `upperright` are tuples.

# Examples

```julia-repl
julia> pixels = [x*NamedColor("blue") + 
                    (1-x)*NamedColor("red") 
                        for x in 0:0.1:1, y in 0:0.1:1]
julia> PixelMap(pixels, (0,0), (1,1))
PixelMap(<11×11>,[0,1]×[0,1])
```
