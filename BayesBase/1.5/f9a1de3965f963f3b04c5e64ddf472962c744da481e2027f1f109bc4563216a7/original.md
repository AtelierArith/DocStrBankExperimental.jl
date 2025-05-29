```
ArrowheadMatrix{O, T, Z, P} <: AbstractMatrix{O}
```

A structure representing an arrowhead matrix, which is a special type of sparse matrix.

# Fields

  * `α::T`: The scalar value at the bottom-right corner of the matrix.
  * `z::Z`: A vector representing the last row/column (excluding the corner element).
  * `D::P`: A vector representing the diagonal elements (excluding the corner element).

# Constructors

```
ArrowheadMatrix(a::T, z::Z, d::D) where {T,Z,D}
```

Constructs an `ArrowheadMatrix` with the given α, z, and D values. The output type `O` is automatically determined as the promoted type of all input elements.

# Operations

  * Matrix-vector multiplication: `A * x` or `mul!(y, A, x)`
  * Linear system solving: `A \ b` or `ldiv!(x, A, b)`
  * Conversion to dense matrix: `convert(Matrix, A)`
  * Inversion: `inv(A)` (returns an `InvArrowheadMatrix`)

# Examples

```julia
α = 2.0
z = [1.0, 2.0, 3.0]
D = [4.0, 5.0, 6.0]
A = ArrowheadMatrix(α, z, D)

# Matrix-vector multiplication
x = [1.0, 2.0, 3.0, 4.0]
y = A * x

# Solving linear system
b = [7.0, 8.0, 9.0, 10.0]
x = A \ b

# Convert to dense matrix
dense_A = convert(Matrix, A)
```

# Notes

  * The matrix is singular if α - dot(z ./ D, z) = 0 or if any element of D is zero.
  * For best performance, use `ldiv!` for solving linear systems when possible.
