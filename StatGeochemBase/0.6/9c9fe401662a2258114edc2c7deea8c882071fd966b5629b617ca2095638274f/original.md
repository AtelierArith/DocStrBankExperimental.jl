```julia
inpolygon(x,y,point)
```

Check if a 2D polygon defined by the arrays `x`, `y` contains a given `point`. Returns boolean (true or false)

### Examples

```julia
julia> x = [0, 1, 1, 0];

julia> y = [0, 0, 1, 1];

julia> inpolygon(x, y, (0.5,0.5))
true

julia> inpolygon(x, y, (0.5,1.5))
false
```
