```
tosimplehrep(constraints::AbstractVector{<:HalfSpace}; [n]::Int=0)
```

Return the simple H-representation $Ax ≤ b$ from a list of linear constraints.

### Input

  * `constraints` – a list of linear constraints
  * `n`           – (optional; default: `0`) dimension of the constraints

### Output

The tuple `(A, b)` where `A` is the matrix of normal directions and `b` is the vector of offsets.

### Notes

The parameter `n` can be used to create a matrix with no constraints but a non-zero dimension. If `n` ≤ 0, this method takes the dimension of the first constraint.
