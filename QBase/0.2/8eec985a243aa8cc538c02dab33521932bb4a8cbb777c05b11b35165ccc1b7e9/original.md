```
is_orthonormal_basis(basis_vecs ::  Vector;  atol=ATOL ::  Float64) :: Bool
```

Returns `true` if `basis_vecs` ``{|\psi*j\rangle}*{j=1}^n forms an orthonormal basis:

$$
\langle \psi_j |\psi_j \rangle = 1 \quad \text{and} \quad \langle \psi_j | \psi_{k} \rangle = 0
$$

for all $j$ and $k$ where $j\neq k$.
