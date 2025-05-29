```
vrep(lines::LineIt; d::FullDim)
```

Creates an affine space of full dimension `d` from the list of lines `lines`.

### Examples

```julia
vrep([Line([1, 0, 0]), Line([0, 1, 0])])
```

creates the 2-dimensional affine subspace containing all the points $(x_1, x_2, 0)$, i.e. the $x_1$$x_2$-plane.
