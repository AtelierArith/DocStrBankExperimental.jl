```julia
get_resolution(
    escher_location::String
) -> NamedTuple{(:height, :width, :x, :y), <:NTuple{4, Any}}

```

Return a named tuple with the dimensions of the escher map. Fields are `height`, `width`, `x`, and `y`. If the fields are  missing in the supplied map, return `missing`. 

# Example

```
h,w,x,y = get_resolution(map_location)

f = Figure(resolution = (x, y))
```
