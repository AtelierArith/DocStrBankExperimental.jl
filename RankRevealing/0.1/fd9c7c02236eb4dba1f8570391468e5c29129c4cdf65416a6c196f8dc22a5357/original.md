```
PLUQ <: Factorizarion
```

Matrix factorization type for the full `LU` factorization of any rectangular matrix `A` over an arbitrary numeric field. This is the return type of [`pluq`](@ref).

The factorization satisfies

```
P * [L ; M] * [U V] * Q == A
```

| Component | Description                          |
|:--------- |:------------------------------------ |
| `F.L`     | Full-rank unit lower triangular part |
| `F.U`     | Full-rank upper triangular part      |
| `F.M`     | Remainder of the row dimension       |
| `F.V`     | Remainder of the column dimension    |
| `F.P`     | row-wise permutation `Matrix`        |
| `F.Q`     | column-wise permutation `Matrix`     |
| `F.p`     | row-wise permutation `Vector`        |
| `F.q`     | column-wise permutation `Matrix`     |

Iteration and destructuring produce the components in the order `p`, `L`, `U`, `V`, `M`, q`.

Both `L` and `U` are square full-rank matrices with the same rank as `A`.
