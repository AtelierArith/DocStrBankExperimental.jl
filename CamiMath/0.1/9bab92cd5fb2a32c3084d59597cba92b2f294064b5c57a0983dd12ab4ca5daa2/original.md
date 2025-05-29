```
istriangle(a::Real, b::Real, c::Real)
```

Triangle condition for a triangle of sides `a`, `b` and `c`.

#### Example:

```
julia> istriangle(3, 4, 5)
true

julia> istriangle(1//2, 1, 1.5)
true
```
