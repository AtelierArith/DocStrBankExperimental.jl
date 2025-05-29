```
galerkin_matrix!(
    [f::Function], A::AbstractMatrix, B::AbstractBSplineBasis, [deriv = (Derivative(0), Derivative(0))];
    [quadrature],
)
```

Fill preallocated Galerkin matrix.

The matrix may be a `Hermitian` view, in which case only one half of the matrix will be filled. Note that, for the matrix to be symmetric, both derivative orders in `deriv` must be the same.

More generally, it is possible to combine different functional bases by passing a tuple of `AbstractBSplineBasis` as `B`.

See [`galerkin_matrix`](@ref) for details on arguments.
