```
hstack(ps::Union{Plot,Context}...)
hstack(ps::Vector)
```

Arrange plots into a horizontal row.  Use `context()` as a placeholder for an empty panel.  Heterogeneous vectors must be typed.  See also [`vstack`](@ref), [`gridstack`](@ref), and [`Geom.subplot_grid`](@ref).

# Examples

```
p1 = plot(x=[1,2], y=[3,4], Geom.line);
p2 = Compose.context();
hstack(p1, p2)
hstack(Union{Plot,Compose.Context}[p1, p2])
```
