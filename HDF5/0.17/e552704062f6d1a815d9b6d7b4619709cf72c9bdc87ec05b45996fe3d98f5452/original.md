```
dataspace(dims::Tuple; max_dims::Tuple=dims)
dataspace(dims::Tuple, max_dims::Tuple)
```

Construct a simple `Dataspace` for the given dimensions `dims`. The maximum dimensions `maxdims` specifies the maximum possible size: `-1` can be used to indicate unlimited dimensions.
