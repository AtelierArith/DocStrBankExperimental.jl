```
Field(backend, grid, loc, type=eltype(grid); halo=1)
```

Constructs a field on a structured grid at the specified location.

## Arguments:

  * `backend`: The backend to use for memory allocation.
  * `grid`: The structured grid on which the field is constructed.
  * `loc`: The location or locations on the grid where the field is constructed.
  * `type`: The element type of the field. Defaults to the element type of the grid.
  * `halo`: The halo size for the field. Defaults to 1.
