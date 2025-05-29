```
CuDim3(x)

CuDim3((x,))
CuDim3((x, y))
CuDim3((x, y, x))
```

A type used to specify dimensions, consisting of 3 integers for respectively the `x`, `y` and `z` dimension. Unspecified dimensions default to `1`.

Often accepted as argument through the `CuDim` type alias, eg. in the case of [`cudacall`](@ref) or [`CUDA.launch`](@ref), allowing to pass dimensions as a plain integer or a tuple without having to construct an explicit `CuDim3` object.
