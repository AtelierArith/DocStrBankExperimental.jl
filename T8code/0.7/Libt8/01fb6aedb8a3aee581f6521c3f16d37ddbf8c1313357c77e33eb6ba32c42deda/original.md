```
t8_geometry_linear_new()
```

Create a new linear geometry. The geometry is only all tree types and as many vertices as the tree type has. The vertices are saved via the t8*cmesh*set*tree*vertices function. Sets the dimension and the name to "t8_geom_linear"

# Returns

A pointer to an allocated t8_geometry_linear struct, as if the t8*geometry*linear () constructor was called.

### Prototype

```c
t8_geometry_c * t8_geometry_linear_new ();
```
