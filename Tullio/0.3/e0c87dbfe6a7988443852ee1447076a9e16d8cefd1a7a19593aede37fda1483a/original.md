```
@tullio C[i,k] := A[i,j] * B[j,k]
@tullio F[i,k] := $α * D[i].field[j] * E[col=k, row=j] + $β
```

This is a replacement for `@einsum` which understands a bit more syntax. The expression on the right is summed over all possible valued of the free index `k`, and `:=` makes a new array `C`, while `=` and `+=` would write into an existing one. Scalar arguments should have a dollar sign, like `$α` or `A[i,$γ]`.

```
@tullio G[i,j] := M[i+x+1, j+y+1] * K[x,y]
@tullio H[i,j] := M[2i+x, 2j+y]  (x in -1:1, y in -1:1)
```

Shifts and scaling of indices are allowed, including shifts by other indices. Ranges can be provided as shown, for under-constrained indices. If they are over-constrained, shifted indices run over the intersection allowed by all constraints, while un-shifted indices demand agreement between them (e.g. `axes(A,2) == axes(B,1)` above).

```
@tullio (*) L[i] := A[J[k]+2, i] / B[k]^2
```

This is a product instead of a sum, which could also enabled by writing `L[i] *= ...` (in-place). You can use any reduction function such as `@tullio (max) M[i,j] := ...`. Indexing by `J[k]+2` here demands `issubset(J, axes(A,1) .- 2)`.

```
@tullio N[j] := sqrt <| M[i,j]^2
```

Pipe operators `|>` and `<|` apply a function after the sum, here `N ≈ map(norm, eachcol(M))`. Underscores create functions, e.g. `|> sqrt(_ / V[i])` where clearly `i` must not have been summed.

See the readme for further options.
