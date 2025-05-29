```
hrep(hyperplanes::HyperPlaneIt; d::FullDim)
```

Creates an affine space of full dimension `d` from the list of hyperplanes `hyperplanes`.

### Examples

```julia
hrep([HyperPlane([0, 1, 0], 1), HyperPlane([0, 0, 1], 0)])
```

creates the 1-dimensional affine subspace containing all the points $(x_1, 0, 0)$, i.e. the $x_1$-axis.

```julia
hrep([HyperPlane([1, 1], 1), HyperPlane([1, 0], 0)])
```

creates the 0-dimensional affine subspace only containing the point $(0, 1)$.
