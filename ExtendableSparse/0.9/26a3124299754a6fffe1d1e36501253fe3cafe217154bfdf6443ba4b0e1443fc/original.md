```julia
fdrand(, nx; ...)
fdrand(, nx, ny; ...)
fdrand(, nx, ny, nz; matrixtype, update, rand, symmetric)
fdrand(nx; ...)

```

Create matrix  for a mock  finite difference operator for  a diffusion problem with random coefficients on a unit hypercube $\Omega\subset\mathbb R^d$. with $d=1$ if  `nx>1 && ny==1 && nz==1`, $d=2$ if  `nx>1 && ny>1 && nz==1` and $d=3$ if  `nx>1 && ny>1 && nz>1` . In the symmetric case it corresponds to

$$
    \begin{align*}
             -\nabla a \nabla u &= f&&  \text{in}\;  \Omega  \\
    a\nabla u\cdot \vec n + bu &=g && \text{on}\;  \partial\Omega
    \end{align*}
$$

The matrix is irreducibly diagonally dominant, has positive main diagonal entries  and nonpositive off-diagonal entries, hence it has the M-Property. Therefore, its inverse will be a dense matrix with positive entries, and the spectral radius of the  Jacobi iteration matrix $ho(I-D(A)^{-1}A)<1$ .

Moreover, in the symmetric case, it is positive definite.

Parameters+ default values:

|         Parameter + default vale | Description                               |
| --------------------------------:|:----------------------------------------- |
|                             `nx` | Number of unknowns in x direction         |
|                             `ny` | Number of unknowns in y direction         |
|                             `nz` | Number of unknowns in z direction         |
|   `matrixtype = SparseMatrixCSC` | Matrix type                               |
| `update = (A,v,i,j)-> A[i,j]+=v` | Element update function                   |
|              `rand =()-> rand()` | Random number generator                   |
|                 `symmetric=true` | Whether to create symmetric matrix or not |

The sparsity structure is fixed to an orthogonal grid, resulting in a 3, 5 or 7 diagonal matrix depending on dimension. The entries are random unless e.g.  `rand=()->1` is passed as random number generator. Tested for Matrix, SparseMatrixCSC,  ExtendableSparseMatrix, Tridiagonal, SparseMatrixLNK and `:COO`
