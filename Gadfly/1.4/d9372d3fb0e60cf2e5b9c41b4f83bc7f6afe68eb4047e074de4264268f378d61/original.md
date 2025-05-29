```
vstack(ps::Union{Plot,Context}...)
vstack(ps::Vector)
```

Arrange plots into a vertical column.  Use `context()` as a placeholder for an empty panel.  Heterogeneous vectors must be typed.  See also [`hstack`](@ref), [`gridstack`](@ref), and [`Geom.subplot_grid`](@ref).

# Examples

```
p1 = plot(x=[1,2], y=[3,4], Geom.line);
p2 = Compose.context();
vstack(p1, p2)
vstack(Union{Plot,Compose.Context}[p1, p2])
```
