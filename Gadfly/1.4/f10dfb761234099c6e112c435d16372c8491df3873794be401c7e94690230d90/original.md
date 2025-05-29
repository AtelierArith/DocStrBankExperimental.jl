```
gridstack(ps::Matrix{Union{Plot,Context}})
```

Arrange plots into a rectangular array.  Use `context()` as a placeholder for an empty panel.  Heterogeneous matrices must be typed.  See also [`hstack`](@ref) and [`vstack`](@ref).

# Examples

```
p1 = plot(x=[1,2], y=[3,4], Geom.line);
p2 = Compose.context();
gridstack([p1 p1; p1 p1])
gridstack(Union{Plot,Compose.Context}[p1 p2; p2 p1])
```
