```
vmag(V, grid, I...)
```

Compute the magnitude of a vector field `V` at a given grid location `I` in a structured grid `grid`.

## Arguments

  * `V`: A named tuple representing the vector field, where each component is an `AbstractField`.
  * `grid`: The structured grid on which the vector field is defined.
  * `I...`: The indices specifying the location on the grid.
