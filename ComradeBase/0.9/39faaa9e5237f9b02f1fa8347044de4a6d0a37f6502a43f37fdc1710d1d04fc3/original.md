```
UnstructuredDomain(dims::NamedTuple; executor=Serial(), header=ComradeBase.NoHeader)
```

Builds an unstructured grid (really a vector of points) from the dimensions `dims`. The `executor` is used controls how the grid is computed when calling `visibilitymap` or `intensitymap`. The default is `Serial` which mean regular CPU computations. For threaded execution use [`ThreadsEx()`](@ref) or load `OhMyThreads.jl` to uses their schedulers.

Note that unlike `RectiGrid` which assigns dimensions to the grid points, `UnstructuredDomain` does not. This is becuase the grid is unstructured the points are a cloud in a space
