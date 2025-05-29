```
skeleton(mesh, dim)
```

Returns a mesh comprising the `dim`-dimensional sub cells of `mesh`. For example to retrieve the edges of a given surface `mesh`,

```julia
edges = skelton(mesh, 1)
```
