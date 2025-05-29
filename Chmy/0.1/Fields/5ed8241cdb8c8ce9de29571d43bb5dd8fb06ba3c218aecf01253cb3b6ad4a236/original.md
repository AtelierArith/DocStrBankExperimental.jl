```
VectorField(backend::Backend, grid::StructuredGrid{N}, args...; kwargs...) where {N}
```

Create a vector field in the form of a `NamedTuple` on the given `grid` using the specified `backend`. With each component being a `Field`.

## Arguments:

  * `backend::Backend`: The backend to be used for computation.
  * `grid::StructuredGrid{N}`: The structured grid defining the computational domain.
  * `args...`: Additional positional arguments to pass to the `Field` constructor.
  * `kwargs...`: Additional keyword arguments to pass to the `Field` constructor.
