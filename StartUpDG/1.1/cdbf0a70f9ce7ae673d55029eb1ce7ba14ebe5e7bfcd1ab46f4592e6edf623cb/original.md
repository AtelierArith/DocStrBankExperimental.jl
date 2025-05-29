```
make_periodic(md::MeshData{Dim}, is_periodic...) where {Dim}
make_periodic(md::MeshData{Dim}, is_periodic = ntuple(x -> true, Dim)) where {Dim}
make_periodic(md::MeshData, is_periodic = true)
```

Returns new MeshData such that the node maps `mapP` and face maps `FToF` are now periodic. Here, `is_periodic` is a tuple of `Bool` indicating whether or not to impose periodic BCs in the `x`,`y`, or `z` coordinate.
