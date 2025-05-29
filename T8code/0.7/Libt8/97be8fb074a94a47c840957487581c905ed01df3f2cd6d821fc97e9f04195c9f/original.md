```
t8_geometry_lagrange_new()
```

Create a new Lagrange geometry of a given dimension. The geometry is compatible with all tree types and uses as many vertices as the number of Lagrange basis functions used for the mapping. The vertices are saved via the t8*cmesh*set*tree*vertices function. Sets the name to "t8_geom_lagrange"

# Returns

A pointer to an allocated t8_geometry_lagrange struct, as if the t8*geometry*lagrange () constructor was called.

### Prototype

```c
t8_geometry_c * t8_geometry_lagrange_new ();
```
