```
TensorField(backend::Backend, grid::StructuredGrid{3}, args...; kwargs...)
```

Create a 3D tensor field in the form of a named tuple on the given `grid` using the specified `backend`, with components `xx`, `yy`, `zz`, `xy`, `xz`, and `yz` each being a `Field`.

## Arguments:

  * `backend::Backend`: The backend to be used for computation.
  * `grid::StructuredGrid{3}`: The 3D structured grid defining the computational domain.
  * `args...`: Additional positional arguments to pass to the `Field` constructor.
  * `kwargs...`: Additional keyword arguments to pass to the `Field` constructor.
