```
MatrixDerivativeOperator{T <: Real}
MatrixDerivativeOperator(xmin, xmax, nodes, weights, D, accuracy_order, source)
```

A derivative operator on a nonperiodic grid with scalar type `T` computing a derivative as matrix vector product. This type is designed to make it easy to experiment with new operators given in matrix form.

An instance of this type can be constructed by passing the endpoints `xmin`, `xmax` of the desired grid as well as the `nodes`, `weights`, and the derivative operator `D::AbstractMatrix` on a reference interval, assuming that the `nodes` contain the boundary points of the reference interval. `source` is the source of coefficients and can be `nothing` for experimentation.
