```
InvArrowheadMatrix{O, T, Z, P} <: AbstractMatrix{O}
```

A wrapper structure representing the inverse of an `ArrowheadMatrix`.

This structure doesn't explicitly compute or store the inverse matrix. Instead, it stores a reference to the original `ArrowheadMatrix` and implements efficient operations that leverage the special structure of the arrowhead matrix.

# Fields

  * `A::ArrowheadMatrix{O, T, Z, P}`: The original `ArrowheadMatrix` being inverted.

# Constructors

```
InvArrowheadMatrix(A::ArrowheadMatrix{O, T, Z, P})
```

Constructs an `InvArrowheadMatrix` by wrapping the given `ArrowheadMatrix`.

# Operations

  * Matrix-vector multiplication: `A_inv * x` or `mul!(y, A_inv, x)` (Equivalent to solving the system A * y = x)
  * Linear system solving: `A_inv \ x` (Equivalent to multiplication by the original matrix: A * x)
  * Conversion to dense matrix: `convert(Matrix, A_inv)` (Computes and returns the actual inverse as a dense matrix)

# Examples

```julia
α = 2.0
z = [1.0, 2.0, 3.0]
D = [4.0, 5.0, 6.0]
A = ArrowheadMatrix(α, z, D)
A_inv = inv(A)  # Returns an InvArrowheadMatrix

# Multiplication (equivalent to solving A * y = x)
x = [1.0, 2.0, 3.0, 4.0]
y = A_inv * x

# Division (equivalent to multiplying by A)
b = [5.0, 6.0, 7.0, 8.0]
x = A_inv \ b

# Convert to dense inverse matrix
dense_inv_A = convert(Matrix, A_inv)
```

# Notes

  * The inverse exists only if the original `ArrowheadMatrix` is non-singular.
  * Operations with `InvArrowheadMatrix` do not explicitly compute the inverse, but instead solve the corresponding system with the original matrix.

# See Also

  * [`ArrowheadMatrix`](@ref): The original arrowhead matrix structure.
