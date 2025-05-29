```
polytopath(ptlist)
```

Convert a polygon to a Path object.

```julia
@draw drawpath(polytopath(ngon(O, 145, 5, vertices = true)), action = :fill)
```
