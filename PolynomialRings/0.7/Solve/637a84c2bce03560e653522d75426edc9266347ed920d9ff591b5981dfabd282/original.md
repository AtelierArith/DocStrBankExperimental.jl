```
x = matrix_solve_affine(f, y, dims, Type=eltype(y))
```

Return the solution `x` to the equation

```
``f(x) = y``
```

where $x$ is assumed to be a matrix of size `dims`, and `f` is assumed to be a linear map over `Type`.

Note: I haven't really considered the proper semantics when type(x) is not necessarily equal to type(y), and the behaviour of this function may (will) change when I do.
