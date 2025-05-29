```
gram_schmidt_orthogonalisation(x::QQMatrix)
```

Takes the columns of $x$ as the generators of a subset of $\mathbb{Q}^m$ and returns a matrix whose columns are an orthogonal generating set for the same subspace.

# Examples

```jldctest
julia> S = matrix_space(QQ, 3, 3);

julia> A = S([4 7 3; 2 9 1; 0 5 3])
[4   7   3]
[2   9   1]
[0   5   3]

julia> B = gram_schmidt_orthogonalisation(A)
[4   -11//5     95//123]
[2    22//5   -190//123]
[0        5    209//123]
```
