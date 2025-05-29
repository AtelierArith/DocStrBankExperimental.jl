```
t8_geometry_zero_new()
```

Create a new zero geometry. The geometry is only all tree types and as many vertices as the tree type has. The vertices are saved via the t8*cmesh*set*tree*vertices function. Sets the dimension and the name to "t8_geom_zero_"

# Returns

A pointer to an allocated t8_geometry_zero struct, as if the t8*geometry*zero () constructor was called.

### Prototype

```c
t8_geometry_c * t8_geometry_zero_new ();
```
